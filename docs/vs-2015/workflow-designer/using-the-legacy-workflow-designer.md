---
title: Using the Legacy Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302793"
---
# <a name="using-the-legacy-workflow-designer"></a>Использование конструктора рабочих процессов для прежних версий
[!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий, входящий в состав [!INCLUDE[vs2010](../includes/vs2010-md.md)], можно использовать для приложений, работающих с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 It is accessed by selecting either the **.NET Framework 3.0** option or the **.NET Framework 3.5** option in the drop down list at the top of the **New Project** window. The default option in [!INCLUDE[vs2010](../includes/vs2010-md.md)] is **.NET Framework 4** which is used to create [!INCLUDE[wf](../includes/wf-md.md)] applications that target the [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] предоставляет способ создания с помощью графических средств приложений [!INCLUDE[wf](../includes/wf-md.md)] с использованием знакомого пользовательского интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Приложения [!INCLUDE[wf](../includes/wf-md.md)] состоят из этапов рабочего процесса, называемых действиями. To create a workflow, compose activities on the design surface by dragging their respective activity designers from **Toolbox** onto the design surface.

 В следующей таблице перечислены основные возможности [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для Windows Workflow Foundation.

|Возможность|Описание|
|-------------|-----------------|
|Действие перетаскивания|Drag activities from the **Toolbox** onto the design surface to create a workflow.|
|обозреватель свойств|The standard **Properties** window in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] is used to configure the properties of an activity.|
|Масштаб|The binoculars **Zoom Level** icon is located below the vertical scroll bar on the right side of the design surface. Click the binoculars and select a zoom percentage to cause the workflow graphic to zoom in or out. You can also use the **Pan** icon magnifying glass cursor options to zoom in and out.|
|Сдвиг|The **Pan** icon, a circle that contains four crossed arrows pointing in four directions, is located below the vertical scroll bar on the right side of the design surface just below the binoculars zoom icon. При нажатии значка панорамирования во всплывающем меню предлагаются следующие варианты курсора:<br /><br /> -   The **Zoom In** magnifying glass cursor lets you zoom in by clicking the design surface.<br />-   The **Zoom Out** magnifying glass cursor lets you zoom out by clicking the design surface.<br />-   The **Navigation Tool** hand cursor lets you "grab" and shift the view of a workflow in the design surface.<br />-   The **Default** arrow cursor lets you switch from the other cursors back to the default arrow cursor.|
|Автоматическая прокрутка|Возможно, если рабочий процесс очень большой, возникнет необходимость разместить действие за границами видимой области рабочей области конструктора. С помощь расширений [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно перенести действие непосредственно к границе рабочей области конструктора, за которую необходимо поместить действие. Представление рабочей области конструктора автоматически прокручивается в этом направлении.|
|Смарт-теги|Действия, которые настроены не полностью или с ошибками, помечаются значком с восклицательным знаком. Можно щелкнуть этот значок и просмотреть в раскрывающемся списке ошибки конфигурации, которые существуют в действии. You can then use the **Properties** window to configure the activity appropriately. После того, как все свойства действия настроены правильно, значок в виде восклицательного знака исчезает.|

## <a name="in-this-section"></a>Содержание
 [Окна рабочих процессов в Visual Studio (для прежних версий)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)

 [Представления последовательных рабочих процессов (для прежних версий)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)

 [Использование тем в рабочих процессах (для прежних версий)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Использование конструктора рабочих процессов конечного автомата для прежних версий](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)

 [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>См. также раздел
 [Developing Workflows](https://go.microsoft.com/fwlink?LinkID=65010)