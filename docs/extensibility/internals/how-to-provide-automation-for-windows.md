---
title: Как выполнить Автоматизация для Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37cb183f8b48211da87b03128d5839cf64aca985
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069758"
---
# <a name="how-to-provide-automation-for-windows"></a>Как выполнить Автоматизация для окон
Вы можете предоставить автоматизация для окон документов и средств. Предоставление автоматизации рекомендуется всякий раз, когда вы хотите сделать объекты автоматизации доступными в окне и среде уже не предоставить объект готовые службы автоматизации, как в случае со списком задач.

## <a name="automation-for-tool-windows"></a>Автоматизация для окон инструментов
 Среды обеспечивает автоматизацию в окне инструментов, возвращая стандартный <xref:EnvDTE.Window> объекта, как описано в следующей процедуре:

### <a name="to-provide-automation-for-tool-windows"></a>Для обеспечения автоматизации окна инструментов

1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду со <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> как `VSFPROPID` для получения `Window` объекта.

2.  Когда вызывающий объект запрашивает объект автоматизации определенного VSPackage для вашего окна инструментов через <xref:EnvDTE.Window.Object%2A>, среда вызывает метод `QueryInterface` для `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, или `IDispatch` интерфейсов. Оба `IExtensibleObject` и `IVsExtensibleObject` предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.

3.  Когда среде затем вызывает метод `GetAutomationObject` метод `NULL`, ответ, передав резервного объекта определенного VSPackage.

4.  Если вызов `QueryInterface` для `IExtensibleObject` и `IVsExtensibleObject` завершается ошибкой, то среда вызывает `QueryInterface` для `IDispatch`.

## <a name="automation-for-document-windows"></a>Автоматизация для окон документов
 Стандартный <xref:EnvDTE.Document> объекта также доступна из среды, несмотря на то, что редактор может иметь собственную реализацию <xref:EnvDTE.Document> объекта путем реализации `IExtensibleObject` интерфейс и реагирование на них `GetAutomationObject`.

 Кроме того, редактор можно предоставить объект автоматизации определенного VSPackage, полученные через <xref:EnvDTE.Document.Object%2A> метод путем реализации `IVsExtensibleObject` или `IExtensibleObject` интерфейсов. [Примеры VSSDK](http://aka.ms/vs2015sdksamples) участвует объект автоматизации конкретного документа RTF.

## <a name="see-also"></a>См. также
    
<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>