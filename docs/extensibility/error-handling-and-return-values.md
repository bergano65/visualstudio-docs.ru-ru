---
title: Обработка ошибок и возвращаемые значения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cfbeef2de041cfd71fbf163d7860d903a6cb59e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135521"
---
# <a name="error-handling-and-return-values"></a>Обработка ошибок и возвращаемые значения
Пакеты VSPackage и COM используют ту же архитектуру для ошибки. `SetErrorInfo` И `GetErrorInfo` функции являются частью интерфейса (API) Win32. Любой VSPackage в интегрированной среде разработки (IDE) может вызывать эти глобальные API-интерфейсов Win32 для записи информации об ошибке при получении уведомления об ошибках. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет сборок взаимодействия для управления сведений об ошибке.  
  
## <a name="interop-methods"></a>Методы взаимодействия  
 Для удобства в Интегрированной среде разработки предоставляет метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, чтобы использовать вместо того чтобы вызывать API-интерфейсы Win32. В управляемом коде используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. При возникновении ошибки `HRESULT` поступает на уровне, где должен отображаться сообщение об ошибке (это часто объект реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> обработчик команд), интегрированная среда разработки использует другой метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, чтобы отобразить окно сообщения. В управляемом коде используется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> метод.  
  
 Как разработчик VSPackage обычно реализуют объекты COM `ISupportErrorInfo`. `ISupportErrorInfo` Интерфейс гарантирует, что сведения об ошибке можно переместить по вертикали в цепочке вызовов. Объекты, которые могут использоваться между процессами или в потоки должны поддерживать `ISupportErrorInfo` чтобы убедиться, что сведения об ошибке правильно маршалировать вызывающему объекту.  
  
 Все объекты, которые связаны с пакеты VSPackage и, которые участвуют в расширении возможностей интегрированной среды разработки, включая фабрик редакторов, редакторы, иерархии и предоставляемые службы, должны поддерживать сведения об ошибке. Хотя эти объекты VSPackage для реализации интегрированной среды разработки не требует `ISupportErrorInfo`, рекомендуется всегда.  
  
 IDE отвечает за reporting сведения об ошибке и отображение ее пользователю [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] всякий раз, когда `HRESULT` распространяется в интегрированную среду разработки. IDE также представляет собой механизм для создания `ErrorInfo` объектов.  
  
## <a name="general-guidelines"></a>Общие рекомендации  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> методы задания и отчеты об ошибках, которые являются внутренними для реализации пакета VSPackage. Тем не менее как правило, выполните следующие рекомендации для обработки сообщений об ошибках в пакете VSPackage.  
  
-   Реализуйте `ISupportErrorInfo` в объектах VSPackage COM.  
  
-   Создать механизм, который вызывает для отчетов об ошибках <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод в объекты, реализующие <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Разрешить отображать ошибки пользователям с помощью интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> метод.  
  
## <a name="error-information-in-the-ide"></a>Сведения об ошибке в Интегрированной среде разработки  
 Следующие правила указать способ обработки сведений об ошибках в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки:  
  
-   Как стратегии безопасности, чтобы гарантировать, что ошибка устаревшие сведения не выводятся для пользователей, функции, вызывающие <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> следует вначале вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод. Передайте `null` очистить кэшированные ошибок перед вызов элемента, который может задать новые сведения об ошибке.  
  
-   Разрешены только функции, которые непосредственно не передают сообщения об ошибках для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод, если они возвращают ошибку `HRESULT`. Допускается использование снимите `ErrorInfo` запись на функцию или при возврате <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Единственное исключение из этого правила — когда вызов возвращает ошибку `HRESULT` от которого получающая сторона может явно восстановить или игнорировать.  
  
-   Любая сторона, которая явно не обрабатывает ошибку, `HRESULT` необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод с <xref:Microsoft.VisualStudio.VSConstants.S_OK>. В противном случае `ErrorInfo` объекта может быть случайно использовано, когда другая сторона создает ошибку без предоставления своих собственных `ErrorInfo`.  
  
-   Все методы, которые происходят ошибки `HRESULT` , рекомендуется вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод, чтобы предоставить сведения об ошибке. Если возвращенный `HRESULT` является специальной `FACILITY_ITF` ошибки, а затем метод требуется для предоставления строгим `ErrorInfo`объекта. Если стандартная системная ошибка возвращена следующая ошибка (например, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>и т. д.) допустима вернуть код ошибки без явного вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод. Как защитного кодирования стратегия, когда исходящие ошибка `HRESULT` (включая системные ошибки), всегда вызывайте метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод, с помощью `ErrorInfo` сбоя более подробно описывающий или `null`.  
  
-   Все функции, возвращающие ошибку от другого вызова необходимо передать на информации, полученного из сбой вызова в `HRESULT` без изменения `ErrorInfo` объекта.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (автоматизация компонентов)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Интерфейс ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)