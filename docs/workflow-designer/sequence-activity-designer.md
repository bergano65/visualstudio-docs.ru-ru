---
title: "Конструктор действия Sequence | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Конструктор действия Sequence
Операция <xref:System.Activities.Statements.Sequence> содержит упорядоченную коллекцию дочерних действий, которые выполняются последовательно.  
  
 Другой способ упорядоченно выполнить набор операций заключается в использовании операции <xref:System.Activities.Statements.Flowchart>.Подумайте об использовании [Блок\-схема](../workflow-designer/flowchart-activity-designer.md), если требуется диаграммное моделирование работы простого выполнения программы с ветвлением или циклом.  
  
## Использование конструктора действий Sequence  
 Чтобы добавить операцию <xref:System.Activities.Statements.Sequence>, перетащите конструктор действий «**Последовательность**» из **Области элементов** и поместите его в область [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Чтобы добавить дочернюю операцию к операции <xref:System.Activities.Statements.Sequence>, перетащите другую операцию из **Области элементов** и переместите ее на треугольник в диалоговом окне с подсказкой «Перетащить действие сюда».  
  
### Свойства действия Sequence в конструкторе рабочих процессов  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Sequence> и описано их использование в конструкторе.Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Sequence> в заголовке.Значение по умолчанию — Sequence.Значение можно дополнительно изменить в сетке свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то, что значения <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## См. также  
 [Блок\-схема](../workflow-designer/flowchart-activity-designer.md)   
 [Управление потоком](../workflow-designer/control-flow-activity-designers.md)