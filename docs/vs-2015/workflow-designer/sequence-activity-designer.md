---
title: Конструктор действия последовательности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 47743feae8c256aa0ddb4e3270aca32b108aa5d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994005"
---
# <a name="sequence-activity-designer"></a>Конструктор действия Sequence
Операция <xref:System.Activities.Statements.Sequence> содержит упорядоченную коллекцию дочерних действий, которые выполняются последовательно.  
  
 Другой способ упорядоченно выполнить набор операций заключается в использовании операции <xref:System.Activities.Statements.Flowchart>. Рассмотрите возможность использования [блок-схема](../workflow-designer/flowchart-activity-designer.md) при наличии простого с ветвлением или выполнением программы, которую требуется диаграммное.  
  
## <a name="using-the-sequence-activity-designer"></a>Использование конструктора действий Sequence  
 Чтобы добавить <xref:System.Activities.Statements.Sequence> действие, перетащите **последовательности** конструктор из **элементов** и сбросьте его в [!INCLUDE[wfd1](../includes/wfd1-md.md)] поверхности. Чтобы добавить дочернее действие к <xref:System.Activities.Statements.Sequence> действие, перетащите другую операцию из **элементов** и поместите его в треугольник в поле с текстом подсказки «Перетащить действие сюда».  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Свойства действия Sequence в конструкторе рабочих процессов  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Sequence> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Sequence> в заголовке. Значение по умолчанию - Sequence. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
  
## <a name="see-also"></a>См. также  
 [Блок-схема](../workflow-designer/flowchart-activity-designer.md)   
 [Поток управления](../workflow-designer/control-flow-activity-designers.md)