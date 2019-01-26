---
title: Расширение модели объекта базового проекта | Документация Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c04192e2377c58e93f37634de28fc32c0e2bc74
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986258"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Расширение модели объекта базового проекта

Подтип проекта может расширить объектную модель автоматизации базового проекта в следующих местах:

-   Project.Extender («\<ProjectSubtypeName > "): Это позволяет подтипом проекта, пройдя пользовательских методов из объекта <xref:EnvDTE.Project> объекта. Подтип проекта расширители автоматизации можно использовать для предоставления `Project` объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения следует предлагать свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (соответствующий `itemid` значение [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)) CATID.

-   ProjectItem.Extender("\<ProjectSubtypeName>"): Это позволяет подтипом проекта, пройдя пользовательских методов объекта от конкретного <xref:EnvDTE.ProjectItem> объекта в проекте. Подтип проекта можно использовать расширения автоматизации для предоставления этого объекта. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения необходимо предложить свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующий требуемой <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties: Данная коллекция предоставляет свойства конфигурациями `Project` объекта. Дополнительные сведения о свойствах `Project` см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтип проекта можно использовать расширения автоматизации для добавления его свойства в данную коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения необходимо предложить свой объект для `VSHPROPID_BrowseObjectCATID` из VSHPROPID2 (соответствующий `itemid` значение [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>), из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.

-   Configuration.Properties: Данная коллекция предоставляет свойства, зависимые от конфигурации проекта для конкретной конфигурации (например, Debug). Дополнительные сведения см. в разделе <xref:EnvDTE.Configuration>. Подтип проекта можно использовать расширения автоматизации для добавления его свойства в данную коллекцию. <xref:EnvDTE80.IInternalExtenderProvider> Интерфейс, реализованный в главный проект подтип средства инвентаризации программного обеспечения предлагает свой объект для этого идентификатор CATID `VSHPROPID_CfgBrowseObjectCATID` (соответствующий `itemid` значение [VSITEMID. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>Интерфейс используется для различения один объект обзора конфигурации из другого.

## <a name="see-also"></a>См. также

<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>