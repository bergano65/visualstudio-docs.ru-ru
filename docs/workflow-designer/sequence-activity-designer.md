---
title: Конструктор действия последовательности конструктор рабочих процессов
description: Узнайте, как действие Sequence содержит упорядоченную коллекцию дочерних действий, выполняемых по порядку.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9e7e6e9114405bc1575e0256dd63211a4fb6d08
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433977"
---
# <a name="sequence-activity-designer"></a>Конструктор действия Sequence

Операция <xref:System.Activities.Statements.Sequence> содержит упорядоченную коллекцию дочерних действий, которые выполняются последовательно.

Другой способ упорядоченно выполнить набор операций заключается в использовании операции <xref:System.Activities.Statements.Flowchart>. Используйте блок- [схему](../workflow-designer/flowchart-activity-designer.md) , если у вас есть простой поток ветвления или циклическая программа, которую требуется смоделировать диаграмматикалли.

## <a name="using-the-sequence-activity-designer"></a>Использование конструктора действий Sequence

Чтобы добавить <xref:System.Activities.Statements.Sequence> действие, перетащите конструктор действий **последовательности** из **области элементов** в область Конструктор рабочих процессов. Чтобы добавить дочернее действие к этому <xref:System.Activities.Statements.Sequence> действию, перетащите другое действие из **панели элементов** и поместите его на треугольник в поле с текстом подсказки "перетащите действие сюда".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Свойства действия Sequence в конструкторе рабочих процессов

В следующей таблице показаны свойства <xref:System.Activities.Statements.Sequence> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Sequence> в заголовке. Значение по умолчанию - Sequence. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также раздел

- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)