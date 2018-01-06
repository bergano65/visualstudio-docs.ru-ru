---
title: "ForEach&lt;T&gt; конструктора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 6016947237274d65d3b59954d783c2a31f3d2b91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; конструктора действий
Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> свойств в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>. Значение по умолчанию — ForEach < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации. Для задания <xref:System.Activities.Statements.ForEach%601.Values%2A>, введите команду [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] выражения в **значения** поле на **ForEach < T\>**  действия конструктора или в сетке свойств.|  
|*TypeArgument*|Да|Тип элементов в <xref:System.Activities.Statements.ForEach%601.Values%2A> коллекции, указанное в универсальном параметре *T*. По умолчанию *TypeArgument* равно **Int32**. Чтобы изменить тип, измените значение *TypeArgument* поле со списком в сетке свойств.|  
  
 По умолчанию именем итератора цикла является **элемент**. Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>См. также  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)