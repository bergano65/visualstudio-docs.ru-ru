---
title: Конструктор рабочих процессов - ForEach&lt;T&gt; конструктора действий
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99531f690e9dcbd1b35453acd17f1c52b8afb1d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836220"
---
# <a name="foreachlttgt-activity-designer"></a>По каждому элементу&lt;T&gt; конструктора действий

Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> свойств в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ForEach%601.Values%2A>, введите выражение Visual Basic в **значения** поле **ForEach < T\>**  действие конструктора или в сетке свойств.|
|*TypeArgument*|Да|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, указанной в универсальном параметре *T*. По умолчанию *TypeArgument* присваивается **Int32**. Чтобы изменить тип, измените значение *TypeArgument* поле со списком в сетке свойств.|

По умолчанию именем итератора цикла является **элемент**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>См. также

- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)