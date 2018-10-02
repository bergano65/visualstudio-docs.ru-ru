---
title: Конструктор действия последовательности | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d3f005ba61ad93eb2b1dd2663831b33a133b64e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573225"
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