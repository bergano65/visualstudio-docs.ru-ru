---
title: Конструктор действий &gt; ParallelForEach &lt;T | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672605"
---
# <a name="parallelforeachlttgt-activity-designer"></a>Конструктор действий &gt; ParallelForEach &lt;T
Действие <xref:System.Activities.Statements.ParallelForEach%601> перечисляет элементы коллекции и выполняет вложенную инструкцию для каждого элемента коллекции параллельно, асинхронно в том же потоке. Это действие управления потоком следует использовать вместо действия <xref:System.Activities.Statements.Sequence>, если ожидается, что вложенные действия перейдут в режим бездействия.

 Действие <xref:System.Activities.Statements.ParallelForEach%601> имеет свойство <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Действие <xref:System.Activities.Statements.ParallelForEach%601> вычисляет это свойство после завершения каждой ветви кода. Если значение равно **true**, то действие <xref:System.Activities.Statements.ParallelForEach%601> завершается без выполнения других ветвей. Если <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> не принимает **значение true**, действие <xref:System.Activities.Statements.ParallelForEach%601> завершается после завершения всех его дочерних действий.

## <a name="the-parallelforeacht-activity"></a>Действие ParallelForEach \<T >
 <xref:System.Activities.Statements.ParallelForEach%601> перечисляет свои значения и планирует для каждого из них <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Планируются только <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Выполнение тела зависит от перехода <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> в состояние простоя.

 Если <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> не переходит в состояние простоя, то выполнение производится в обратном порядке, так как запланированные действия помещаются в стек, то есть последнее запланированное действие выполняется первым. Например, если имеется коллекция {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> и для записи значения используется параметр **WriteLine** в качестве текста. В консоли есть 4, 3, 2 и 1 распечатанные. Это происходит потому, что **WriteLine** не переходит в режим простоя, поэтому после **выполнения 4 действий** , запланированных, они выполнялись с использованием поведения стека (первая за последней).

 Но если в <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> имеются действия, которые могут перейти в состояние простоя, например <xref:System.ServiceModel.Activities.Receive> или <xref:System.Activities.Statements.Delay>, Нет необходимости ожидать их завершения. <xref:System.Activities.Statements.ParallelForEach%601> переходит к следующему запланированному действию текста и пытается выполнить его. Если и это действие перешло в режим простоя, то <xref:System.Activities.Statements.ParallelForEach%601> опять переходит к следующему действию тела.

### <a name="using-the-parallelforeacht-activity-designer"></a>Использование конструктора действий > ParallelForEach \<T
 Конструктор действий **ParallelForEach \<T >** можно найти в категории **поток управления** **панели элементов**, щелкнув вкладку **область элементов** в левой части [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выберите  **Панели инструментов** из меню **вид** или CTRL + ALT + X.)

 Конструктор действий **ParallelForEach \<T >** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)]ную поверхность, где обычно размещаются конструкторы действий, например, внутри конструктора действий **последовательности** . После его удаления в [!INCLUDE[wfd2](../includes/wfd2-md.md)] создается действие <xref:System.Activities.Statements.ParallelForEach%601>, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> **\<Int32 > ParallelForEach.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach \<T > свойства в конструктор рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ParallelForEach%601>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **ParallelForEach \<Int32 >** . Значение можно дополнительно изменить в сетке **свойств** или непосредственно в заголовке конструктора операций.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Действие, выполняемое для каждого элемента в коллекции. Чтобы добавить действие <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, перетащите действие из области элементов в поле Body ( **текст** ) в конструкторе действий **ParallelForEach \<T >** с текстом подсказки "перетащите действие сюда".|
|**TypeArgument**|True|Тип элементов в коллекции <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, заданной универсальным параметром *t*. По умолчанию **TypeArgument** имеет значение **Int32**. Чтобы изменить тип T в конструкторе действий **ParallelForEach \<T >** , измените значение поля со списком **TypeArgument** в сетке свойств.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, введите [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в поле **значения** в конструкторе действий **foreach \<T >** в поле с текстом подсказки "введите выражение VB" или в поле " **значения** " в окне " **Свойства** ".|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Оценивается после каждого выполнения итерации. Если результат оценки равен true, то запланированные ожидающие итерации отменяются. Если это свойство не задано, все запланированные инструкции выполняются до завершения.|

 По умолчанию итератор цикла является именованным элементом. Имя переменной итератора можно изменить в поле **foreach** в конструкторе действий **ParallelForEach \<T >** . Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>См. также раздел
 [Поток управления](../workflow-designer/control-flow-activity-designers.md) [параллельной](../workflow-designer/parallel-activity-designer.md) [последовательности](../workflow-designer/sequence-activity-designer.md)