---
title: Конструктор действий конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115163"
---
# <a name="while-activity-designer"></a>Конструктор действия While

Действие <xref:System.Activities.Statements.While> выполняет действие, содержащееся в его <xref:System.Activities.Statements.While.Body%2A>, в то время как указанное <xref:System.Activities.Statements.While.Condition%2A> принимает **значение true**. Вложенное действие может быть не выполнено ни разу. Если вложенное действие должно быть выполнено хотя бы один раз, пользуйтесь вместо этого действием <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Свойства While в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.While>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательное|Метрики|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ложь|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.While> в заголовке. Значение по умолчанию - While. Значение можно изменить в окне **Свойства** или непосредственно в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.While.Body%2A>|Ложь|Содержит действие, выполняемое, когда <xref:System.Activities.Statements.While.Condition%2A> принимает **значение true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Да|Содержит выражение Visual Basic, которое вычисляется, чтобы определить, должно ли выполняться действие в <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>См. также:

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
