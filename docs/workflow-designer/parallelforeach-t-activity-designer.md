---
title: '&lt; &gt; Конструктор активности ParallelForEach T'
description: В конструктор рабочих процессов Узнайте, как действие ParallelForEach <T> перечисляет элементы коллекции и выполняет внедренный оператор для каждого элемента коллекции в параллельном режиме.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b35bcb6fcd1dc2ac3826d5dccb17ff764979321
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968753"
---
# <a name="parallelforeach-activity-designer"></a>Конструктор действия ParallelForEach

Действие <xref:System.Activities.Statements.ParallelForEach%601> перечисляет элементы коллекции и выполняет вложенную инструкцию для каждого элемента коллекции параллельно, асинхронно в том же потоке. Это действие управления потоком следует использовать вместо действия <xref:System.Activities.Statements.Sequence>, если ожидается, что вложенные действия перейдут в режим бездействия.

<xref:System.Activities.Statements.ParallelForEach%601>Действие имеет <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> свойство, которое содержит указанное пользователем Visual Basic выражение. Действие <xref:System.Activities.Statements.ParallelForEach%601> вычисляет это свойство после завершения каждой ветви кода. Если значение равно **true**, <xref:System.Activities.Statements.ParallelForEach%601> действие завершается без выполнения других ветвей. Если значение не <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> принимает **значение true**, <xref:System.Activities.Statements.ParallelForEach%601> действие завершается после завершения всех его дочерних действий.

## <a name="the-parallelforeacht-activity"></a>Действие ParallelForEach<T \>

<xref:System.Activities.Statements.ParallelForEach%601> Перечисляет значения и планирует <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> для каждого значения, по которому выполняется перечисление. Планируются только <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Выполнение тела зависит от перехода <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> в состояние простоя.

Если <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> не переходит в состояние простоя, то выполнение производится в обратном порядке, так как запланированные действия помещаются в стек, то есть последнее запланированное действие выполняется первым. Например, если имеется коллекция {1,2,3,4} в <xref:System.Activities.Statements.ParallelForEach%601> и для записи значения используется параметр **WriteLine** в качестве текста. В консоли есть 4, 3, 2 и 1 распечатанные. Это происходит потому, что **WriteLine** не переходит в режим простоя, поэтому после **выполнения 4 действий** , запланированных, они выполнялись с использованием поведения стека (первая за последней).

Но если в <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> имеются действия, которые могут перейти в состояние простоя, например <xref:System.ServiceModel.Activities.Receive> или <xref:System.Activities.Statements.Delay>, Нет необходимости ожидать их завершения. <xref:System.Activities.Statements.ParallelForEach%601> переходит к следующему запланированному действию текста и пытается выполнить его. Если и это действие перешло в режим простоя, то <xref:System.Activities.Statements.ParallelForEach%601> опять переходит к следующему действию тела.

### <a name="using-the-parallelforeacht-activity-designer"></a>Использование \<T> конструктора действий ParallelForEach

Доступ к конструктору действий **ParallelForEach \<T>** в категории " **поток управления** " **панели элементов**.

Конструктор **действий \<T> ParallelForEach** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где бы они ни находились, в то время как конструкторы действий обычно размещаются, например, внутри конструктора действий **последовательности** . После его удаления в конструктор рабочих процессов создается <xref:System.Activities.Statements.ParallelForEach%601> действие, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> **ParallelForEach<Int32 \> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>Свойства ParallelForEach<T \> в конструктор рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ParallelForEach%601>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию **— \<Int32> ParallelForEach**. Значение можно дополнительно изменить в сетке **свойств** или непосредственно в заголовке конструктора операций.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Действие, выполняемое для каждого элемента в коллекции. Чтобы добавить <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> действие, перетащите действие из области элементов в поле **текст** в конструкторе действия **ParallelForEach \<T>** с текстом подсказки "перетащите действие сюда".|
|**TypeArgument**|True|Тип элементов в <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> коллекции, заданном универсальным параметром *T*. По умолчанию **TypeArgument** имеет значение **Int32**. Чтобы изменить тип T в конструкторе действий **ParallelForEach<\> T** , измените значение поля со списком **TypeArgument** в сетке свойств.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> , введите Visual Basic выражение в поле **значения** в конструкторе действий **foreach<T \>** в поле с текстом подсказки "введите выражение VB" или в поле " **значения** " в окне " **Свойства** ".|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Оценивается после каждого выполнения итерации. Если результат оценки равен true, то запланированные ожидающие итерации отменяются. Если это свойство не задано, все запланированные инструкции выполняются до завершения.|

По умолчанию итератор цикла является именованным элементом. Имя переменной итератора можно изменить в поле **foreach** конструктора действий **ParallelForEach \<T>** . Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>См. также раздел

- [Последовательность](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)