---
title: '&lt; &gt; Конструктор действий ParallelForEach T | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672605"
---
# <a name="parallelforeachlttgt-activity-designer"></a>&lt; &gt; Конструктор активности ParallelForEach T
Действие <xref:System.Activities.Statements.ParallelForEach%601> перечисляет элементы коллекции и выполняет вложенную инструкцию для каждого элемента коллекции параллельно, асинхронно в том же потоке. Это действие управления потоком следует использовать вместо действия <xref:System.Activities.Statements.Sequence>, если ожидается, что вложенные действия перейдут в режим бездействия.

 Действие <xref:System.Activities.Statements.ParallelForEach%601> имеет свойство <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, содержащее указанное пользователем выражение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Действие <xref:System.Activities.Statements.ParallelForEach%601> вычисляет это свойство после завершения каждой ветви кода. Если значение равно **true**, <xref:System.Activities.Statements.ParallelForEach%601> действие завершается без выполнения других ветвей. Если значение не <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> принимает **значение true**, <xref:System.Activities.Statements.ParallelForEach%601> действие завершается после завершения всех его дочерних действий.

## <a name="the-parallelforeacht-activity"></a>Действие ParallelForEach \<T>
 <xref:System.Activities.Statements.ParallelForEach%601> Перечисляет значения и планирует <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> для каждого значения, по которому выполняется перечисление. Планируются только <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Выполнение тела зависит от перехода <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> в состояние простоя.

 Если <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> не переходит в состояние простоя, то выполнение производится в обратном порядке, так как запланированные действия помещаются в стек, то есть последнее запланированное действие выполняется первым. Например, если имеется коллекция {1,2,3,4} в <xref:System.Activities.Statements.ParallelForEach%601> и для записи значения используется параметр **WriteLine** в качестве текста. В консоли есть 4, 3, 2 и 1 распечатанные. Это происходит потому, что **WriteLine** не переходит в режим простоя, поэтому после **выполнения 4 действий** , запланированных, они выполнялись с использованием поведения стека (первая за последней).

 Но если в <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> имеются действия, которые могут перейти в состояние простоя, например <xref:System.ServiceModel.Activities.Receive> или <xref:System.Activities.Statements.Delay>, Нет необходимости ожидать их завершения. <xref:System.Activities.Statements.ParallelForEach%601> переходит к следующему запланированному действию текста и пытается выполнить его. Если и это действие перешло в режим простоя, то <xref:System.Activities.Statements.ParallelForEach%601> опять переходит к следующему действию тела.

### <a name="using-the-parallelforeacht-activity-designer"></a>Использование \<T> конструктора действий ParallelForEach
 Конструктор **действий \<T> ParallelForEach** можно найти в категории **поток управления** **панели элементов**, щелкнув вкладку **область элементов** в левой части окна [!INCLUDE[wfd2](../includes/wfd2-md.md)] (или выберите **панель инструментов** в меню **вид** или нажмите клавиши CTRL + ALT + X).

 Конструктор **действий \<T> ParallelForEach** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где бы они ни находились, как обычно размещаются конструкторы действий, например внутри конструктора действий **последовательности** . После его удаления в [!INCLUDE[wfd2](../includes/wfd2-md.md)] создается <xref:System.Activities.Statements.ParallelForEach%601> действие, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach \<Int32> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>\<T>Свойства ParallelForEach в конструктор рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ParallelForEach%601>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию **— \<Int32> ParallelForEach**. Значение можно дополнительно изменить в сетке **свойств** или непосредственно в заголовке конструктора операций.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Неверно|Действие, выполняемое для каждого элемента в коллекции. Чтобы добавить <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> действие, перетащите действие из области элементов в поле **текст** в конструкторе действия **ParallelForEach \<T> ** с текстом подсказки "перетащите действие сюда".|
|**TypeArgument**|Верно|Тип элементов в <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> коллекции, заданном универсальным параметром *T*. По умолчанию **TypeArgument** имеет значение **Int32**. Чтобы изменить тип T в конструкторе **действия \<T> ParallelForEach** , измените значение поля со списком **TypeArgument** в сетке свойств.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Верно|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> , введите [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в поле **значения** конструктора действий **ForEach \<T> ** в поле с текстом подсказки "введите выражение VB" или в поле " **значения** " в окне " **Свойства** ".|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Оценивается после каждого выполнения итерации. Если результат оценки равен true, то запланированные ожидающие итерации отменяются. Если это свойство не задано, все запланированные инструкции выполняются до завершения.|

 По умолчанию итератор цикла является именованным элементом. Имя переменной итератора можно изменить в поле **foreach** конструктора действий **ParallelForEach \<T> ** . Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>См. также:
 [Поток управления](../workflow-designer/control-flow-activity-designers.md) [параллельной](../workflow-designer/parallel-activity-designer.md) [последовательности](../workflow-designer/sequence-activity-designer.md)