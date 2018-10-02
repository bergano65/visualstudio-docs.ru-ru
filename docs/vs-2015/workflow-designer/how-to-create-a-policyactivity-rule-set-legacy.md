---
title: 'Практическое: создать набор правил PolicyActivity (для прежних версий) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e0ecab43d582f0901374fd5b1807c54bc8fcf03c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572359"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Как создать набор правил PolicyActivity (для прежних версий)
В этом разделе описывается создание набора правил действия политики с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 После перетаскивания **политики** элемент действия из **элементов** в область конструктора рабочих процессов необходимо выбрать существующее правило или создать новый набор правил для [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) действия. Выберите существующий набор с помощью правил [правила задайте диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md) и наборы правил создаются с помощью [правила задайте диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Вы можете открыть [правила задайте диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) диалоговое окно по двойному щелчку на [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) действие, которое находится в области конструктора рабочих процессов.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Выбор или создание набора правил для действия PolicyActivity  
  
1.  Щелкните правой кнопкой мыши [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), а затем нажмите кнопку **свойства** открыть **свойства** окна.  
  
2.  Нажмите кнопку **RuleSetReference** свойство.  
  
3.  Выполните одно из следующих действий.  
  
    -   Нажмите кнопку **RuleSetReference** многоточие **[...]** , а затем выберите существующий набор правил в [правила задайте диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Далее перейдите к шагу 10.  
  
         -или-  
  
    -   Введите имя набора правил. Нажмите кнопку **RuleSetReference** многоточие **[...]** , а затем выберите **изменить** в [правила задайте диалоговое окно Выбор (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         - или -  
  
    -   Введите имя набора правил. Разверните **RuleSetReference** свойство и выберите кнопку с многоточием **[...]**  в **RuleSet Definition** свойство.  
  
         [Правила задайте диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) открывает.  
  
4.  В [правила задайте диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), нажмите кнопку **добавить правило** Чтобы добавить новое правило в набор правил.  
  
5.  Введите **имя**, **приоритет**, и **повторной оценки** свойства, или оставить значения по умолчанию.  
  
6.  Введите текст для **условие**.  
  
7.  Введите текст для **действия Then** и **действия Else**.  
  
8.  Нажмите кнопку **добавить правило** еще раз, чтобы добавить еще одно правило.  
  
9. Завершив настройку, нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Выберите правило набора диалоговое окно (для прежних версий)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Набор правил диалоговое окно редактора (для прежних версий)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Использование действия Policy](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)