---
title: "Как создать набор правил PolicyActivity (для прежних версий) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "действие PolicyActivity, создание наборов правил"
  - "действие PolicyActivity, выбор наборов правил"
  - "диалоговое окно "Редактор набора правил""
  - "наборы правил, создание для действия PolicyActivity"
  - "диалоговое окно «Выбрать набор правил»"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Как создать набор правил PolicyActivity (для прежних версий)
В этом разделе описывается создание набора правил действия политики с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 После перетаскивания элемента действия **Policy** из **Области элементов** в область конструктора рабочих процессов можно либо выбрать существующее правило, либо создать новый набор правил для действия [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019).Существующий набор правил выбирается с использованием диалогового окна [Диалоговое окно «Выбор набора правил» \(для прежних версий\)](../workflow-designer/select-rule-set-dialog-box-legacy.md), новые наборы правил создаются с использованием диалогового окна [Диалоговое окно «Редактор набора правил» \(для прежних версий\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Диалоговое окно [Диалоговое окно «Редактор набора правил» \(для прежних версий\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) можно открыть по двойному щелчку на действии [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), расположенном на рабочей области конструктора рабочих процессов.  
  
### Выбор или создание набора правил для действия PolicyActivity  
  
1.  Щелкните правой кнопкой мыши по действию [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), выберите команду **Свойства**, чтобы открыть окно **Свойства**.  
  
2.  Щелкните свойство **RuleSetReference**.  
  
3.  Выполните одно из следующих действий.  
  
    -   Нажмите кнопку с многоточием **RuleSetReference\[…\]**, далее выберите существующий набор правил в диалоговое окно [Диалоговое окно «Выбор набора правил» \(для прежних версий\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).Далее перейдите к шагу 10.  
  
         — или —  
  
    -   Введите имя набора правил.Нажмите кнопку с многоточием **RuleSetReference\[…\]**, далее выберите **Изменить** в диалоговом окне [Диалоговое окно «Выбор набора правил» \(для прежних версий\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         или  
  
    -   Введите имя набора правил.Раскройте свойство **RuleSetReference** и нажмите кнопку с многоточием **\[…\]** в свойстве **RuleSet Definition**.  
  
         Откроется диалоговое окно [Диалоговое окно «Редактор набора правил» \(для прежних версий\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
4.  В диалоговом окне [Диалоговое окно «Редактор набора правил» \(для прежних версий\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) нажмите **Добавить правило**, чтобы добавить новое правило в набор правил.  
  
5.  Введите свойства **Имя**, **Приоритет** и **Повторная оценка** или сохраните значения по умолчанию.  
  
6.  Введите текст в поле **Условие**.  
  
7.  Введите текст для полей **Действия THEN** и **Действия ELSE**.  
  
8.  Чтобы добавить другое правило снова нажмите **Добавить правило**.  
  
9. По завершении нажмите кнопку **ОК**.  
  
## См. также  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Диалоговое окно «Выбор набора правил» \(для прежних версий\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Диалоговое окно «Редактор набора правил» \(для прежних версий\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Использование действия Policy](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)