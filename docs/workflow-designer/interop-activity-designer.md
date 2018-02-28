---
title: "Конструктор действия Interop | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 726bc2fa995d819b0e554e11439c85f9fdf19243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="interop-activity-designer"></a>Конструктор действия Interop
**Взаимодействия** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Interop> действия.  
  
## <a name="the-interop-activity"></a>Действие Interop  
 Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.  
  
### <a name="using-the-interop-activity-designer"></a>Использование конструктора операций Interop  
 **Взаимодействия** конструктора действий можно найти в **миграции** категории **элементов**, который нажав **элементов**вкладка (либо выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 [Миграции](../workflow-designer/migration-activity-designers.md) категорию, которая содержит <xref:System.Activities.Statements.Interop> действия проявится только в **элементов** Если проект предназначен для полной [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Для проектов C# можно переопределить проект на использование [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **свойства**. На **приложения** выберите **NET Framework 4** в диалоговом окне **требуемой версии .NET framework**. Выберите **Да** кнопку в **изменение версии .NET Framework** диалоговое окно, которое отображает запрос на подтверждение этого изменения.  
  
 Для проектов VB можно переопределить проект на использование [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] , щелкнув проект в **обозревателе решений** и выбрав **свойства**. На **компиляции** щелкните **Дополнительные параметры компиляции** кнопки. Выберите **.Net Framework 4** из **списке** и нажмите кнопку **ОК**. Нажмите кнопку **Да** кнопку в **изменение версии .NET Framework** диалоговое окно, которое отображает запрос на подтверждение этого изменения.  
  
 **Взаимодействия** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Interop> действия по умолчанию **DisplayName** взаимодействия. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **взаимодействия** конструктора или в **DisplayName** поле сетки свойств.  
  
 Нажмите кнопку **нажмите, чтобы просмотреть...**  текста в **ActivityType** поле, либо на **взаимодействия** действия конструктора или в сетке свойств, чтобы открыть **Обзор и Выбор типа .net тип** диалоговое окно. Отображаются только типы действий рабочего процесса 3.0 или 3.5 (т. е. только типы, являющиеся производными от <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../test/includes/crabout_md.md)]используется для указания типа, в разделе [Обзор и Выбор типа .NET-диалоговое](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) раздела.  
  
### <a name="the-interop-properties"></a>Свойства Interop  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Interop> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Interop>. Значение по умолчанию - Interop. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>. Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>См. также  
 [Миграция](../workflow-designer/migration-activity-designers.md)