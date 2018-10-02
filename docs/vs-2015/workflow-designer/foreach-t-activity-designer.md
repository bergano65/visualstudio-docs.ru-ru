---
title: По каждому элементу&lt;T&gt; конструктора действий | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b118eb62f3055486e26f9d90a4e3abb74fe38660
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563779"
---
# <a name="foreachlttgt-activity-designer"></a>По каждому элементу&lt;T&gt; конструктора действий
Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>По каждому элементу\<T > свойства в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach\<Int32 >. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ForEach%601.Values%2A>, введите значение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в **значения** поле на **ForEach\<T >** действие конструктора или в сетке свойств.|  
|*TypeArgument*|Да|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, указанной в универсальном параметре *T*. По умолчанию *TypeArgument* присваивается **Int32**. Чтобы изменить тип, измените значение *TypeArgument* поле со списком в сетке свойств.|  
  
 По умолчанию именем итератора цикла является **элемент**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>См. также  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)