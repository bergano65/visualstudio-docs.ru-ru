---
title: Конструктор действий «конструктор рабочих процессов по каждому элементу &lt; T» &gt;
description: Узнайте, как <T> действие ForEach выполняет действие, содержащееся в его теле, для каждого элемента в коллекции указанных значений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c594e613d1160794e8310695d61bcc97902caa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876463"
---
# <a name="foreachlttgt-activity-designer"></a>&lt; &gt; Конструктор действий foreach T

Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Свойства ForEach<T \> в конструктор рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach<Int32 \> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ForEach%601.Values%2A> , введите Visual Basic выражение в поле **значения** в конструкторе действий **foreach<T \>** или в сетке свойств.|
|*TypeArgument*|True|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, заданном универсальным параметром *T*. По умолчанию *TypeArgument* имеет значение **Int32**. Чтобы изменить тип, измените значение поля со списком *TypeArgument* в сетке свойств.|

По умолчанию итератор цикла называется **Item**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>См. также раздел

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
