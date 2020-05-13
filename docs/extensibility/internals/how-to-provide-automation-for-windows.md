---
title: 'Как: Обеспечить автоматизацию для Windows Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707955"
---
# <a name="how-to-provide-automation-for-windows"></a>Как: Обеспечить автоматизацию окон

Вы можете обеспечить автоматизацию окон документов и инструментов. Обеспечение автоматизации рекомендуется при желании сделать объекты автоматизации доступными на окне, а среда уже не предоставляет готовый объект автоматизации, как это происходит со списком задач.

## <a name="automation-for-tool-windows"></a>Автоматизация для окон инструментов

Среда обеспечивает автоматизацию на окне <xref:EnvDTE.Window> инструмента, возвращая стандартный объект, как это объясняется в следующей процедуре:

1. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> иметод через окружающую среду с [помощью __VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` в качестве `Window` параметра для получения объекта.

2. Когда абонент запрашивает объект автоматизации, специфичный <xref:EnvDTE.Window.Object%2A>для окна `QueryInterface` `IExtensibleObject`инструмента, через него требуется среда <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>или `IDispatch` интерфейсы. И `IExtensibleObject` `IVsExtensibleObject` обеспечить <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> метод.

3. Когда среда вызывает `GetAutomationObject` проходящий `NULL`метод, отвечайте, передавая ваш объект, специфичный для VSPackage.

4. Если `QueryInterface` призыв `IExtensibleObject` `IVsExtensibleObject` ы не требует `QueryInterface` и `IDispatch`терпит неудачу, то окружающая среда требует .

## <a name="automation-for-document-windows"></a>Автоматизация окон документов

Стандартный <xref:EnvDTE.Document> объект также доступен из среды, хотя редактор <xref:EnvDTE.Document> может иметь `IExtensibleObject` свою собственную `GetAutomationObject`реализацию объекта путем реализации интерфейса и реагирования на .

Кроме того, редактор может предоставить объект автоматизации, разработанный с помощью <xref:EnvDTE.Document.Object%2A> метода, для реализации `IVsExtensibleObject` `IExtensibleObject` или интерфейсов. [Образцы VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) вносят в себя объект автоматизации, специфичный для документов RTF.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
