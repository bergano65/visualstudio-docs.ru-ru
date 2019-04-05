---
title: По каждому элементу&lt;T&gt; конструктора действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992410"
---
# <a name="foreachlttgt-activity-designer"></a>По каждому элементу&lt;T&gt; конструктора действий
Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>По каждому элементу\<T > свойства в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach\<Int32 >. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ForEach%601.Values%2A>, введите значение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в **значения** поле на **ForEach\<T >** действие конструктора или в сетке свойств.|  
|*TypeArgument*|True|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, указанной в универсальном параметре *T*. По умолчанию *TypeArgument* присваивается **Int32**. Чтобы изменить тип, измените значение *TypeArgument* поле со списком в сетке свойств.|  
  
 По умолчанию именем итератора цикла является **элемент**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>См. также  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)