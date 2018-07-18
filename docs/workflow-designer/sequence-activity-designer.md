---
title: Конструктор рабочих процессов - конструктор действия Sequence
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e72c5b5e43ca037a6d65e3e4980fdb0f89f000f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31972046"
---
# <a name="sequence-activity-designer"></a>Конструктор действия Sequence

Операция <xref:System.Activities.Statements.Sequence> содержит упорядоченную коллекцию дочерних действий, которые выполняются последовательно.

Другой способ упорядоченно выполнить набор операций заключается в использовании операции <xref:System.Activities.Statements.Flowchart>. Рассмотрите возможность использования [блок-схема](../workflow-designer/flowchart-activity-designer.md) при наличии простой ветвление или циклы, который нужно смоделировать diagrammatically поток выполнения программы.

## <a name="using-the-sequence-activity-designer"></a>Использование конструктора действий Sequence

Чтобы добавить <xref:System.Activities.Statements.Sequence> действие, перетащите **последовательности** конструктора действий из **элементов** и поместите его на поверхности конструктора рабочих процессов Windows. Чтобы добавить дочернюю операцию к <xref:System.Activities.Statements.Sequence> действие, перетащите другую операцию из **элементов** и поместите его на треугольник в диалоговом окне с текстом подсказки «Перетащить действие сюда».

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Свойства действия Sequence в конструкторе рабочих процессов

В следующей таблице показаны свойства <xref:System.Activities.Statements.Sequence> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Sequence> в заголовке. Значение по умолчанию - Sequence. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также

- [Блок-схема](../workflow-designer/flowchart-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)