---
title: '&lt; &gt; Конструктор действий foreach T | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656655"
---
# <a name="foreachlttgt-activity-designer"></a>&lt; &gt; Конструктор действий foreach T
Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.

## <a name="foreacht-properties-in-the-workflow-designer"></a>\<T>Свойства foreach в конструктор рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach \<Int32> . Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Верно|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ForEach%601.Values%2A> , введите [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в поле **значения** в конструкторе операций **ForEach \<T> ** или в сетке свойств.|
|*TypeArgument*|Верно|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, заданном универсальным параметром *T*. По умолчанию *TypeArgument* имеет значение **Int32**. Чтобы изменить тип, измените значение поля со списком *TypeArgument* в сетке свойств.|

 По умолчанию итератор цикла называется **Item**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>См. также:
 [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) [Поток управления](../workflow-designer/control-flow-activity-designers.md)