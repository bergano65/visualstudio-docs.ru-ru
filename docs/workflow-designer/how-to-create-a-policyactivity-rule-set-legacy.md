---
title: "Как: создать набор правил PolicyActivity (для прежних версий) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1b57fe5f33bdbc4dfb7ab76856bdd80a3246ea9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Как создать набор правил PolicyActivity (для прежних версий)
В этом разделе описывается создание набора правил действия политики с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 После перетаскивания **политики** элемент действия из **элементов** в область конструктора рабочих процессов, необходимо выбрать существующее правило или создать новый набор правил для [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) действия. Выберите существующее правило, устанавливается с помощью [правила задайте диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md) и создание наборов правил с помощью [задать редактора диалогового окна правила (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Можно открыть [задать редактора диалогового окна правила (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) диалоговое напрямую, дважды щелкнув [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) действия, которое находится в области конструктора рабочих процессов.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Выбор или создание набора правил для действия PolicyActivity  
  
1.  Щелкните правой кнопкой мыши [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), а затем нажмите кнопку **свойства** Открытие **свойства** окна.  
  
2.  Нажмите кнопку **RuleSetReference** свойство.  
  
3.  Выполните одно из следующих действий.  
  
    -   Нажмите кнопку **RuleSetReference** многоточие **[...]** , а затем выберите существующий набор правил в [правила задайте диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Далее перейдите к шагу 10.  
  
         -или-  
  
    -   Введите имя набора правил. Нажмите кнопку **RuleSetReference** многоточие **[...]** , а затем выберите **изменить** в [правила задайте диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         - или -  
  
    -   Введите имя набора правил. Разверните **RuleSetReference** и нажмите кнопку с многоточием **[...]**  в **RuleSet Definition** свойство.  
  
         [Задать редактора диалогового окна правила (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) открывается.  
  
4.  В [задать редактора диалогового окна правила (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), нажмите кнопку **добавить правило** для добавления нового правила в наборе правил.  
  
5.  Введите **имя**, **приоритет**, и **переоценки** свойства, или оставить значения по умолчанию.  
  
6.  Введите текст для **условие**.  
  
7.  Введите текст для **действия Then** и **действия Else**.  
  
8.  Нажмите кнопку **добавить правило** еще раз, чтобы добавить новое правило.  
  
9. Завершив настройку, нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Действие PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Диалоговое окно задания выберите правило (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Набор правил, диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Использование действия политики](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)