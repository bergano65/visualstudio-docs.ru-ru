---
title: Руководство. предоставление автоматизации для Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848854"
---
# <a name="how-to-provide-automation-for-windows"></a>Руководство. предоставление автоматизации для Windows

Вы можете предоставить автоматизацию для окон документов и инструментов. Предоставление автоматизации рекомендуется, если нужно сделать объекты автоматизации доступными в окне, а среда еще не предоставляет готовый объект автоматизации, как это делается в списке задач.

## <a name="automation-for-tool-windows"></a>Автоматизация для окон инструментов

Среда предоставляет автоматизацию для окна инструментов, возвращая стандартный объект <xref:EnvDTE.Window>, как описано в следующей процедуре:

1. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> через среду с [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) в качестве параметра `VSFPROPID`, чтобы получить объект `Window`.

2. Когда вызывающий объект запрашивает в своем окне средства автоматизацию, зависящую от VSPackage, с помощью <xref:EnvDTE.Window.Object%2A>среда вызывает `QueryInterface` для `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>или интерфейсов `IDispatch`. И `IExtensibleObject`, и `IVsExtensibleObject` предоставляют метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Когда среда затем вызывает метод `GetAutomationObject`, передавая `NULL`, ответьте на него, передав объект, относящийся к VSPackage.

4. Если вызов `QueryInterface` для `IExtensibleObject` и `IVsExtensibleObject` завершается сбоем, среда вызывает `QueryInterface` для `IDispatch`.

## <a name="automation-for-document-windows"></a>Автоматизация для окон документов

В среде также доступен стандартный объект <xref:EnvDTE.Document>, хотя редактор может иметь собственную реализацию объекта <xref:EnvDTE.Document>, реализуя интерфейс `IExtensibleObject` и реагируя на `GetAutomationObject`.

Кроме того, редактор может предоставить специфический для VSPackage объект автоматизации, полученный с помощью метода <xref:EnvDTE.Document.Object%2A>, реализуя интерфейсы `IVsExtensibleObject` или `IExtensibleObject`. [Примеры VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) вносят объект автоматизации, относящийся к документу RTF.

## <a name="see-also"></a>См. также:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
