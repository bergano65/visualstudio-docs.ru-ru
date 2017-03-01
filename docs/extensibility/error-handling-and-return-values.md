---
title: "Обработка ошибок и возвращаемые значения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>Обработка ошибок и возвращаемые значения
Пакеты VSPackage и COM используют ту же архитектуру для ошибки. `SetErrorInfo` И `GetErrorInfo` функции являются частью интерфейс (API) Win32. Любой пакет VSPackage в интегрированную среду разработки (IDE) можно вызвать эти глобальные интерфейсы API Win32 для записи информации об ошибке при получении уведомления об ошибках. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет сборок взаимодействия для управления сведениями об ошибке.  
  
## <a name="interop-methods"></a>Методы взаимодействия  
 Для удобства в Интегрированной среде разработки предоставляет метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, чтобы использовать вместо вызова API-интерфейсов Win32.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> В управляемом коде используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> При возникновении ошибки `HRESULT` приходит на уровне, где должен отображаться сообщение об ошибке (это часто объект реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>обработчик команды), интегрированной среды разработки используется другой метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, чтобы отобразить окно сообщения.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> В управляемом коде используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
 Отдельный исполнитель VSPackage COM-объекты обычно реализует `ISupportErrorInfo`. `ISupportErrorInfo` Интерфейс гарантирует, что сведения об ошибке можно перейти по вертикали в цепочке вызовов. Объекты, которые могут быть использованы для процессов или потоков должны поддерживать `ISupportErrorInfo` чтобы убедиться, что сведения об ошибке правильно маршалировать обратно вызывающему.  
  
 Все объекты, которые относятся к VSPackages и участвует в IDE, включая редактор фабрик, редакторы, иерархий, расширение или предлагаемых служб, должны поддерживать сведения об ошибке. Хотя эти объекты VSPackage для реализации интегрированной среды разработки не требуется `ISupportErrorInfo`, рекомендуется всегда.  
  
 IDE отвечает за reporting сведения об ошибке и отображение ее пользователю [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] всякий раз, когда `HRESULT` распространяется в интегрированную среду разработки. IDE также имеет механизм для создания `ErrorInfo` объектов.  
  
## <a name="general-guidelines"></a>Общие рекомендации  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>методов для установки и сообщать об ошибках, которые являются внутренними для реализации VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Однако как правило, придерживайтесь следующих правил для обработки сообщений об ошибках в VSPackage.  
  
-   Реализация `ISupportErrorInfo` в объектах VSPackage COM.  
  
-   Создать механизм, который вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метод в объектах, которые реализуют <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> для отчетов об ошибках  
  
-   Разрешить отображение ошибок пользователей с помощью интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
## <a name="error-information-in-the-ide"></a>Сведения об ошибке в Интегрированной среде разработки  
 Следующие правила указать способ обработки сведений об ошибках в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки:  
  
-   Как стратегии безопасности, чтобы гарантировать, что пользователям, не сообщается информация об ошибке устаревшие функции, вызывающие <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>следует вначале вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Передайте `null` Очистка кэшированных сообщений до вызова ничего, задать новые сведения об ошибке.  
  
-   Функции, которые не передают сообщения об ошибках непосредственно разрешены только для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метода, если они возвращают ошибку `HRESULT`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Можно очистить `ErrorInfo` в операции на функцию или возврат <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Единственное исключение для этого правила — когда вызов возвращает ошибку `HRESULT` от которого получающая сторона может явным образом восстановить или игнорировать.  
  
-   Любая сторона, которая явно не обрабатывает ошибку, `HRESULT` необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метод <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> В противном случае — `ErrorInfo` объект может случайно использовать Если другая сторона создает ошибку, не предоставляя собственные `ErrorInfo`.  
  
-   Все методы, которые происходят ошибки `HRESULT` , рекомендуется вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метод, чтобы предоставить сведения об ошибке.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Если возвращенный `HRESULT` специальный `FACILITY_ITF` ошибки, а затем метод требуется для предоставления верной `ErrorInfo`объекта. Если ошибка стандартная система вернула ошибку (например, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>и т. д.) это допустимо для возврата кода ошибки без явного вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> Как защитного кодирования стратегию, если возникшая ошибка `HRESULT` (включая системные ошибки), следует всегда вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>метод, с помощью `ErrorInfo` описанием причины более подробно или `null`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   Все функции, возвращающие ошибку от другого вызова необходимо передать на информации, полученное от отказавшего вызов в `HRESULT` без изменения `ErrorInfo` объекта.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (автоматизация компонентов)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Интерфейс ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
