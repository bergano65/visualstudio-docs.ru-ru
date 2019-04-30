---
title: Конструктор действия Interop | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952052"
---
# <a name="interop-activity-designer"></a>Конструктор действия Interop
**Взаимодействия** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.Interop> действия.  
  
## <a name="the-interop-activity"></a>Действие Interop  
 Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.  
  
### <a name="using-the-interop-activity-designer"></a>Использование конструктора операций Interop  
 **Взаимодействия** конструктора действий можно найти в **миграции** категории **элементов**, который нажав **элементов**вкладка (Кроме того, выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 [Миграции](../workflow-designer/migration-activity-designers.md) категории, содержащей <xref:System.Activities.Statements.Interop> действия выводится только в **элементов** Если проект предназначен для полной [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 Для проектов C#, вы можете повторно ориентироваться проект для использования полной [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **свойства**. На **приложения** выберите **NET Framework 4** в диалоговом окне **требуемой версии .NET framework**. Выберите **Да** кнопку **изменение версии .NET Framework** диалоговом окне для подтверждения изменения.  
  
 Для проектов Visual Basic, вы можете повторно ориентироваться проект для использования полной [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] щелкните правой кнопкой мыши проект в **обозревателе решений** и выбрав **свойства**. На **компиляции** щелкните **Дополнительные параметры компиляции** кнопки. Выберите **.Net Framework 4** из **списке требуемой версии** и нажмите кнопку **ОК**. Нажмите кнопку **Да** кнопку **изменение версии .NET Framework** диалоговом окне для подтверждения изменения.  
  
 **Взаимодействия** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.Interop> действие по умолчанию **DisplayName** взаимодействия. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **взаимодействия** конструктора действий или в **DisplayName** поле таблицы свойств.  
  
 Нажмите кнопку **нажмите, чтобы просмотреть...** текст в **ActivityType** поле, либо на **взаимодействия** действие конструктора или в сетке свойств, чтобы открыть **Обзор и выбор .net типа** диалоговое окно. Отображаются только типы действий рабочего процесса 3.0 или 3.5 (т. е. только типы, являющиеся производными от <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] в этом окне для указания типа, см. в разделе [Обзор и Выбор типа .NET диалоговое окно](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) раздела.  
  
### <a name="the-interop-properties"></a>Свойства Interop  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Interop> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.Interop>. Значение по умолчанию - Interop. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>. Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>См. также  
 [Миграция](../workflow-designer/migration-activity-designers.md)