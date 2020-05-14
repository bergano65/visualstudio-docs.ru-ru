---
title: Значения обработки ошибок и возврата (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711935"
---
# <a name="error-handling-and-return-values"></a>Значения обработки и возврата ошибок
VSPackages и COM используют одну и ту же архитектуру для ошибок. `SetErrorInfo` Функции `GetErrorInfo` и функции являются частью интерфейса программирования приложений Win32 (API). Любой VSPackage в интегрированной среде разработки (IDE) может вызвать эти глобальные AI Win32 для записи богатой информации об ошибках при получении уведомления об ошибке. Предоставляет [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] интероп-сборки для управления информацией об ошибках.

## <a name="interop-methods"></a>Методы Интероп
 Для удобства, IDE предоставляет метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>чтобы использовать вместо вызова AIS Win32. В управляемом <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>использовании кода . Когда ошибка `HRESULT` приходит на уровне, на котором должно отображаться сообщение об ошибке (это часто является объектом, реализующим обработчик <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> команды), IDE использует другой метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>для отображения соответствующего окна сообщения. В управляемом <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> коде используйте метод.

 Как реалистом VSPackage, объекты `ISupportErrorInfo`COM обычно реализуют. Интерфейс `ISupportErrorInfo` гарантирует, что богатая информация об ошибках может перемещаться вертикально вверх по цепочке вызовов. Объекты, которые могут использоваться в `ISupportErrorInfo` процессах или между потоками, должны поддерживаться, чтобы гарантировать, что информация об ошибке будет надлежащим образом возвращена вызывающему абоненту.

 Все объекты, связанные с VSPackages и участвующие в расширении IDE, включая фабрики редакторов, редакторы, иерархии и предлагаемые услуги, должны поддерживать богатую информацию об ошибках. Хотя IDE не требует реализации этих `ISupportErrorInfo`объектов VSPackage, он всегда поощряется.

 IDE несет ответственность за сообщение информации об ошибках и отображение ее пользователю всякий раз, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] когда `HRESULT` оно распространяется в IDE. IDE также является механизмом `ErrorInfo` создания объектов.

## <a name="general-guidelines"></a>Общие рекомендации
 Вы можете <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> и методы для установки и сообщения об ошибках, которые являются внутренними для реализации VSPackage, а также. Однако, как правило, следуйте этим рекомендациям по обработке сообщений об ошибках в VSPackage:

- Реализация `ISupportErrorInfo` в ваших объектах VSPackage COM.

- Создайте механизм отчетности <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> об ошибке, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>который вызывает метод в объектах, которые реализуются.

- Пусть IDE отображает ошибки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> пользователям с помощью метода.

## <a name="error-information-in-the-ide"></a>Информация об ошибках в IDE
 Следующие правила указывают, как обрабатывать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] информацию об ошибках в IDE:

- В качестве оборонительной стратегии, гарантируя, что информация об <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> зачерх <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ошибках не сообщается пользователям, функции, которые называют метод должен сначала вызвать метод. `null` Пройдите, чтобы очистить кэшированные сообщения об ошибках, прежде чем звонить что-либо, что может установить новую информацию об ошибках.

- Функции, которые непосредственно не сообщают об <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ошибках, могут вызывать `HRESULT`метод только в том случае, если они возвращают ошибку. Допустимо очистить `ErrorInfo` при входе в функцию или <xref:Microsoft.VisualStudio.VSConstants.S_OK>при возвращении. Единственным исключением из этого правила является `HRESULT` возвращение вызова ошибки, из которой принимающая сторона может явно восстановиться или безопасно проигнорировать.

- Любая сторона, которая явно `HRESULT` игнорирует <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> ошибку, должна вызвать метод с <xref:Microsoft.VisualStudio.VSConstants.S_OK>помощью . В противном случае `ErrorInfo` объект может быть случайно использован, когда `ErrorInfo`другая сторона генерирует ошибку, не предоставляя свои собственные.

- Все методы, которые `HRESULT` возникают ошибка рекомендуется вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод, чтобы обеспечить богатую информацию об ошибке. Если возврат `HRESULT` является `FACILITY_ITF` особой ошибкой, то метод `ErrorInfo`необходим для обеспечения надлежащего объекта. Если возвращенная ошибка — это стандартная <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>системная ошибка (например, , и <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>и так далее), <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> то допустимо вернуть код ошибки без явного вызова метода. В качестве стратегии оборонительного кодирования `HRESULT` при возникновении ошибки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (включая `ErrorInfo` системные ошибки) всегда `null`вызывайте метод, либо описывая сбой более подробно, либо.

- Все функции, возвращающие ошибку, возникшую другим вызовом, должны `HRESULT` передавать информацию, полученную от отказающего вызова в неизменяемом объекте. `ErrorInfo`

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Компонентная автоматизация)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Интерфейс ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
