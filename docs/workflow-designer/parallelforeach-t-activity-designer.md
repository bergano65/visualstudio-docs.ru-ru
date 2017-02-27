---
title: "Конструктор действия ParallelForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Конструктор действия ParallelForEach&lt;T&gt;
Действие <xref:System.Activities.Statements.ParallelForEach%601> перечисляет элементы коллекции и выполняет вложенную инструкцию для каждого элемента коллекции параллельно, асинхронно в том же потоке.Это действие управления потоком следует использовать вместо действия <xref:System.Activities.Statements.Sequence>, если ожидается, что вложенные действия перейдут в режим бездействия.  
  
 Действие <xref:System.Activities.Statements.ParallelForEach%601> имеет свойство <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].Действие <xref:System.Activities.Statements.ParallelForEach%601> вычисляет это свойство после завершения каждого участка кода.Если результат вычисления равен **true**, то действие <xref:System.Activities.Statements.ParallelForEach%601> завершается без выполнения других участков кода.Если результат <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> не равен **true**, то действие <xref:System.Activities.Statements.ParallelForEach%601> завершается после того, как все его дочерние действия будут завершены.  
  
## Действие ParallelForEach\<T\>  
 <xref:System.Activities.Statements.ParallelForEach%601> перечисляет свои значения и планирует для каждого из них <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.Планируются только <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.Выполнение тела зависит от перехода <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> в состояние простоя.  
  
 Если <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> не переходит в состояние простоя, то выполнение производится в обратном порядке, так как запланированные действия помещаются в стек, то есть последнее запланированное действие выполняется первым.Например, если в <xref:System.Activities.Statements.ParallelForEach%601> имеется коллекция {1,2,3,4} и **WriteLine** используется в качестве текста для записи значения.На консоль выводятся значения 4, 3, 2, 1.Причина этого заключается в том, что **WriteLine** не переходит в состояние простоя и после 4 запланированных действий **WriteLine** их выполнение производится из стека \(первое запланированное действие выполняется последним\).  
  
 Но если в <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> имеются действия, которые могут перейти в состояние простоя, например <xref:System.ServiceModel.Activities.Receive> или <xref:System.Activities.Statements.Delay>,Нет необходимости ожидать их завершения.<xref:System.Activities.Statements.ParallelForEach%601> переходит к следующему запланированному действию текста и пытается выполнить его.Если и это действие перешло в режим простоя, то <xref:System.Activities.Statements.ParallelForEach%601> опять переходит к следующему действию тела.  
  
### Использование конструктора действия ParallelForEach\<T\>  
 Конструктор действия **ParallelForEach\<T\>** можно найти в категории **Поток управленияОбласти элементов**, открыв вкладку **Область элементов** в левой части [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X\).  
  
 Конструктор действия **ParallelForEach\<T\>** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно помещаются конструкторы, например внутрь конструктора действия **Sequence**.После перетаскивания на [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] создается действие <xref:System.Activities.Statements.ParallelForEach%601>, где по умолчанию содержится <xref:System.Activities.Activity.DisplayName%2A>, равное **ParallelForEach\<Int32\>.**  
  
### Свойства ParallelForEach\<T\> в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ParallelForEach%601>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает понятное отображаемое имя действия конструктора в заголовке.Значение по умолчанию — **ParallelForEach\<Int32\>**.Значение можно изменить в таблице **Свойства** или напрямую в заголовке конструктора действия.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Нет|Действие, выполняемое для каждого элемента в коллекции.Чтобы добавить действие <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, перетащите его с панели элементов в поле **Тело** на конструкторе действия **ParallelForEach\<T\>** с текстом подсказки «Перетащите действие сюда».|  
|**TypeArgument**|Да|Тип элементов из коллекции <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, заданный общим параметром *T*.По умолчанию свойство **TypeArgument** имеет значение **Int32**.Чтобы изменить тип T в конструкторе действия **ParallelForEach\<T\>**, измените значение раскрывающегося списка **TypeArgument** в таблице свойств.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Да|Коллекция элементов для итерации.Чтобы установить <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, введите выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] в поле **Значения** в конструкторе действия **ForEach\<T\>** в поле с текстом подсказки «Введите выражение VB» или в поле **Значения** в окне **Свойства**.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Оценивается после каждого выполнения итерации.Если результат оценки равен true, то запланированные ожидающие итерации отменяются.Если это свойство не задано, все запланированные инструкции выполняются до завершения.|  
  
 По умолчанию итератор цикла является именованным элементом.Можно изменить имя переменной итератора в поле **ForEach** в конструкторе действия **ParallelForEach\<T\>**.Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ParallelForEach%601>.  
  
## См. также  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)