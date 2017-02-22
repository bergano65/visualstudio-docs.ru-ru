---
title: "Конструктор действия Interop | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия Interop
Конструктор операций  **Interop** используется для создания и настройки действия <xref:System.Activities.Statements.Interop>.  
  
## Действие Interop  
 Действие <xref:System.Activities.Statements.Interop> управляет выполнением типов, являющихся производными от <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> в рабочем процессе.  
  
### Использование конструктора операций Interop  
 Конструктор операций  **Interop** можно найти в категории **МиграцияОбласти элементов**, нажав на вкладку **Область элементов** \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Категория [Миграция](../workflow-designer/migration-activity-designers.md), содержащая действие <xref:System.Activities.Statements.Interop>, отображается в **Области элементов**, только если проект предназначен для выполнения в [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Для проектов C\# можно переопределить проект на использование [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] путем щелчка правой кнопкой мыши на проекте в **Обозревателе решений** и выборе окна **Свойства**.На вкладке **Приложение** выберите параметр **.NET Framework 4** в списке **Требуемая версия .NET Framework**.Нажмите кнопку **Да** в диалоговом окне **Изменение версии .NET Framework** для подтверждения изменения.  
  
 Для проектов VB можно переопределить проект на использование [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] путем щелчка правой кнопкой мыши на проекте в **Обозревателе решений** и выборе окна **Свойства**.На вкладке **Компиляция** нажмите кнопку **Дополнительные параметры компиляции**.В списке **Требуемая версия .NET Framework** выберите **.NET Framework 4** и нажмите кнопку **ОК**.Нажмите кнопку **Да** в диалоговом окне **Изменение версии .NET Framework** для подтверждения изменения.  
  
 Конструктор операций  **Interop** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.Interop> со значением по умолчанию **DisplayName** для Interop.<xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций  **Interop** либо в поле **DisplayName** таблицы свойств.  
  
 Нажмите текст **Обзор…** в поле **ActivityType**, либо в конструкторе операций **Interop**, либо в таблице свойств для отображения диалогового окна **Обзор и выбор типа .NET**.Отображаются только типы действий рабочего процесса 3.0 или 3.5 \(т.е., только типы, являющиеся производными от <xref:System.Workflow.ComponentModel.Activity>\).[!INCLUDE[crabout](../test/includes/crabout_md.md)] этого диалогового окна для определения типов см. в разделе [Диалоговое окно "Обзор и выбор типа .NET"](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).  
  
### Свойства Interop  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Interop> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств или в области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.Interop>.Значение по умолчанию — Interop.Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Да|Задает тип действия, содержащегося в действии <xref:System.Activities.Statements.Interop>.Заданный тип должен быть производным от класса <xref:System.Workflow.ComponentModel.Activity>.|  
  
## См. также  
 [Миграция](../workflow-designer/migration-activity-designers.md)