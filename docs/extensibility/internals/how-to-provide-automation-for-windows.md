---
title: Руководство. предоставление автоматизации для Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fec2b9ef6612a294dc70d129cf4bdd3dde843262
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905255"
---
# <a name="how-to-provide-automation-for-windows"></a>Руководство. предоставление автоматизации для Windows

Вы можете предоставить автоматизацию для окон документов и инструментов. Предоставление автоматизации рекомендуется, если нужно сделать объекты автоматизации доступными в окне, а среда еще не предоставляет готовый объект автоматизации, как это делается в списке задач.

## <a name="automation-for-tool-windows"></a>Автоматизация для окон инструментов

Среда предоставляет автоматизацию для окна инструментов, возвращая Стандартный <xref:EnvDTE.Window> объект, как описано в следующей процедуре:

1. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> метод через среду с [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) в качестве `VSFPROPID` параметра для получения `Window` объекта.

2. Когда вызывающий объект запрашивает в своем окне инструментария определяемый пакет VSPackage, <xref:EnvDTE.Window.Object%2A> среда вызывает `QueryInterface` для `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> `IDispatch` интерфейсов, или. `IExtensibleObject`И `IVsExtensibleObject` предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.

3. После того, как среда вызывает `GetAutomationObject` передачу метода `NULL` , ответьте на него, передав объект, относящийся к VSPackage.

4. Если вызывает `QueryInterface` метод `IExtensibleObject` и `IVsExtensibleObject` завершается ошибкой, среда вызывает метод `QueryInterface` для `IDispatch` .

## <a name="automation-for-document-windows"></a>Автоматизация для окон документов

Стандартный <xref:EnvDTE.Document> объект также доступен из среды, хотя редактор может иметь собственную реализацию <xref:EnvDTE.Document> объекта путем реализации `IExtensibleObject` интерфейса и реагирования на `GetAutomationObject` .

Кроме того, редактор может предоставить специфический для VSPackage объект автоматизации, полученный с помощью <xref:EnvDTE.Document.Object%2A> метода, путем реализации `IVsExtensibleObject` `IExtensibleObject` интерфейсов или. [Примеры VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) вносят объект автоматизации, относящийся к документу RTF.

## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
