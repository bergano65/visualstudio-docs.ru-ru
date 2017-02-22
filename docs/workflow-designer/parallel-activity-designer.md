---
title: "Конструктор действия Parallel | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия Parallel
Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.  
  
## Действие Parallel  
 Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>.Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.  
  
 Действие <xref:System.Activities.Statements.Parallel> имеет свойство <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждого участка кода.Если результат вычисления равен **True**, то действие <xref:System.Activities.Statements.Parallel> завершается без выполнения других участков кода.Если условие <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> не равно **True**, то действие <xref:System.Activities.Statements.Parallel> завершается после того, как все его дочерние действия будут завершены.  
  
### Использование конструктора действия Parallel  
 Конструктор действия **Parallel** находится в категории **Поток управленияОбласти элементов**, для доступа к которой необходимо перейти на вкладку **Область элементов** в левой части [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] либо выбрать пункт **Область элементов** в меню **Вид** или нажать CTRL\+ALT\+X.  
  
 Конструктор действий **Parallel** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно помещаются конструкторы, например внутри конструктора операций  **Sequence**.После перетаскивания на [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] создается действие <xref:System.Activities.Statements.Parallel>, где по умолчанию содержится <xref:System.Activities.Activity.DisplayName%2A>, равное **Parallel**  
  
 Чтобы добавить действие в коллекцию <xref:System.Activities.Statements.Parallel.Branches%2A> действия Parallel, перетащите какой\-либо другой конструктор действий из **Области элементов** на треугольник внутри конструктора действий **Parallel**.Треугольники обрамляют действия, которые содержатся в ветвях.Дополнительные действия можно добавить, применяя эту процедуру повторно.Порядок действия можно изменять, перетаскивая их внутри конструктора действий **Parallel**.  
  
### Свойства действия Parallel в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает понятное отображаемое имя действия конструктора в заголовке.Значение по умолчанию — **Parallel**.Значение можно изменить в таблице **Свойства** или напрямую в заголовке конструктора действия.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Да|Содержит коллекцию дочерних действий, которые должны быть выполнены.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Нет|Вычисляется после завершения какой\-либо ветви.Если результат вычисления равен **True**, то запланированные ожидающие выполнения ветви отменяются.Если значение этого свойства не задано или равно **False**, то действие завершается после того, как будут завершены все его дочерние действия.Значение по умолчанию — **null**.|  
  
## См. также  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)