---
title: "Конструктор действия ForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия ForEach&lt;T&gt;
Действие <xref:System.Activities.Statements.ForEach%601> выполняет действие, содержащееся в его теле <xref:System.Activities.Statements.ForEach%601.Body%2A> для каждого элемента указанной коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>.  
  
## Свойства ForEach\<T\> в конструкторе рабочих процессов  
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ForEach%601>, которые применяются чаще всего, и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|------------------|-----------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ForEach%601>.По умолчанию ― ForEach\<Int32\>.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Коллекция элементов для итерации.Для установки <xref:System.Activities.Statements.ForEach%601.Values%2A> введите выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] в поле **Значения** конструктора операций **ForEach\<T\>** или в сетку свойств.|  
|*TypeArgument*|Да|Тип элементов в коллекции <xref:System.Activities.Statements.ForEach%601.Values%2A>, указанный общим параметром *T*.По умолчанию свойство *TypeArgument* имеет значение **Int32**.Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в таблице свойств.|  
  
 По умолчанию именем итератора цикла является **item**.Можно изменить имя переменной итератора в конструкторе операций <xref:System.Activities.Statements.ForEach%601>.Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ForEach%601>.  
  
## См. также  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)