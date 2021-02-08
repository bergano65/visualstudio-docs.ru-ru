---
title: Конструктор действий конструктор рабочих процессов
description: Узнайте, как действие While выполняет действие, содержащееся в его теле, в то время как указанное условие принимает значение true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838000"
---
# <a name="while-activity-designer"></a>Конструктор действия While

<xref:System.Activities.Statements.While>Действие выполняет действие, содержащееся в его <xref:System.Activities.Statements.While.Body%2A> ходе, а заданное <xref:System.Activities.Statements.While.Condition%2A> значение принимает **значение true**. Вложенное действие может быть не выполнено ни разу. Если вложенное действие должно быть выполнено хотя бы один раз, пользуйтесь вместо этого действием <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Свойства While в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.While>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.While> в заголовке. Значение по умолчанию - While. Значение можно изменить в окне **Свойства** или непосредственно в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Содержит действие, выполняемое, пока <xref:System.Activities.Statements.While.Condition%2A> выражение имеет **значение true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Содержит выражение Visual Basic, которое вычисляется, чтобы определить, должно ли выполняться действие в <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>См. также раздел

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
