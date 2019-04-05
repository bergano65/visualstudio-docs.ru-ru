---
title: ParallelForEach&lt;T&gt; конструктора действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 825906f3de1b2d40d96dc19ed45d2a368d889994
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994434"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; конструктора действий
Действие <xref:System.Activities.Statements.ParallelForEach%601> перечисляет элементы коллекции и выполняет вложенную инструкцию для каждого элемента коллекции параллельно, асинхронно в том же потоке. Это действие управления потоком следует использовать вместо действия <xref:System.Activities.Statements.Sequence>, если ожидается, что вложенные действия перейдут в режим бездействия.  
  
 Действие <xref:System.Activities.Statements.ParallelForEach%601> имеет свойство <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Действие <xref:System.Activities.Statements.ParallelForEach%601> вычисляет это свойство после завершения каждой ветви кода. Если результат вычисления равен **true**, а затем <xref:System.Activities.Statements.ParallelForEach%601> действие завершается без выполнения других ветвей. Если <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> не равен значению **true**, а затем <xref:System.Activities.Statements.ParallelForEach%601> действие завершается после завершения всех его дочерних действий.  
  
## <a name="the-parallelforeacht-activity"></a>Действие ParallelForEach\<T > действия  
 <xref:System.Activities.Statements.ParallelForEach%601> перечисляет свои значения и планирует для каждого из них <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Планируются только <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Выполнение тела зависит от перехода <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> в состояние простоя.  
  
 Если <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> не переходит в состояние простоя, то выполнение производится в обратном порядке, так как запланированные действия помещаются в стек, то есть последнее запланированное действие выполняется первым. Например, если у вас есть коллекция {1,2,3,4}в <xref:System.Activities.Statements.ParallelForEach%601> и использовать **WriteLine** как текст для записи значения. На консоль выводятся значения 4, 3, 2, 1. Это обусловлено **WriteLine** не переходит в состояние простоя и после 4 **WriteLine** запланированных действий, их выполнение поведения стека (первый выполняется последним).  
  
 Но если в <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> имеются действия, которые могут перейти в состояние простоя, например <xref:System.ServiceModel.Activities.Receive> или <xref:System.Activities.Statements.Delay>, Нет необходимости ожидать их завершения. <xref:System.Activities.Statements.ParallelForEach%601> переходит к следующему запланированному действию текста и пытается выполнить его. Если и это действие перешло в режим простоя, то <xref:System.Activities.Statements.ParallelForEach%601> опять переходит к следующему действию тела.  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>С помощью ParallelForEach\<T > конструктора действий  
 **ParallelForEach\<T >** конструктора действий можно найти в **поток управления** категории **элементов**, который нажав  **Панель элементов** вкладка в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **ParallelForEach\<T >** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface везде, где обычно помещаются конструкторы, для Например, внутри **последовательности** конструктора действий. После его перетаскивания [!INCLUDE[wfd2](../includes/wfd2-md.md)], он создает <xref:System.Activities.Statements.ParallelForEach%601> действие, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> из **ParallelForEach\<Int32 >.**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach\<T > свойства в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ParallelForEach%601>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **ParallelForEach\<Int32 >**. Можно при необходимости изменить значение в **свойства** сетки или напрямую в заголовке конструктора действий.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Действие, выполняемое для каждого элемента в коллекции. Чтобы добавить <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> действие, перетащите его из области элементов в **текст** поле **ParallelForEach\<T >** конструктора действий с текстом подсказки «Перетащить действие сюда».|  
|**TypeArgument**|True|Тип элементов в <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> коллекции, указанной в универсальном параметре *T*. По умолчанию **TypeArgument** присваивается **Int32**. Чтобы изменить тип T в **ParallelForEach\<T >** конструктора действий, измените значение свойства **TypeArgument** поле со списком в сетке свойств.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Коллекция элементов для итерации. Для задания <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, введите значение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в **значения** поле **ForEach\<T >** конструктора действий, в поле с текстом подсказки «Введите выражение VB» или в **Значения** поле **свойства** окна.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Оценивается после каждого выполнения итерации. Если результат оценки равен true, то запланированные ожидающие итерации отменяются. Если это свойство не задано, все запланированные инструкции выполняются до завершения.|  
  
 По умолчанию итератор цикла является именованным элементом. Можно изменить имя переменной итератора в **ForEach** поле **ParallelForEach\<T >** конструктора действий. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ParallelForEach%601>.  
  
## <a name="see-also"></a>См. также  
 [Последовательности](../workflow-designer/sequence-activity-designer.md)   
 [Параллельный](../workflow-designer/parallel-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)