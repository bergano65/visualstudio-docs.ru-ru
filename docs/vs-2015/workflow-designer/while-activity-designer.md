---
title: Конструктор действия While | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36752df3d8ffbf33b8ea95570d6a4efe8c8cd3be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855402"
---
# <a name="while-activity-designer"></a>Конструктор действия While

<xref:System.Activities.Statements.While> Действия выполняет действие, содержащееся в его <xref:System.Activities.Statements.While.Body%2A> пока указанное условие, результатом которого является **true**. Вложенное действие может быть не выполнено ни разу. Если вложенное действие должно быть выполнено хотя бы один раз, пользуйтесь вместо этого действием <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Свойства While в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.While>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.While> в заголовке. Значение по умолчанию - While. Можно изменить значение в **свойства** окна или напрямую в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Содержит действие, выполняемое при <xref:System.Activities.Statements.While.Condition%2A> принимает значение **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Содержит выражение [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], значение которого определяет, будет ли выполнено действие в <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>См. также

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)