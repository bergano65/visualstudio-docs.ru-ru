---
title: Конструктор действия While | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c5b75a2575a7e8d6eeed4f42a269849bc2df899
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="while-activity-designer"></a>Конструктор действия While
<xref:System.Activities.Statements.While> Действия выполняет действие, содержащееся в его <xref:System.Activities.Statements.While.Body%2A> пока результат вычисления указанного <xref:System.Activities.Statements.While.Condition%2A> равен **true**. Вложенное действие может быть не выполнено ни разу. Если вложенное действие должно быть выполнено хотя бы один раз, пользуйтесь вместо этого действием <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Свойства While в конструкторе рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.While>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.While> в заголовке. Значение по умолчанию - While. Значение можно изменить в **свойства** окна или напрямую в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Содержит действие, выполняемое при <xref:System.Activities.Statements.While.Condition%2A> равен **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Да|Содержит выражение [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], значение которого определяет, будет ли выполнено действие в <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>См. также

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)