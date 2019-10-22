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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663263"
---
# <a name="sequence-activity-designer"></a>Конструктор действия Sequence
Операция <xref:System.Activities.Statements.Sequence> содержит упорядоченную коллекцию дочерних действий, которые выполняются последовательно.

 Другой способ упорядоченно выполнить набор операций заключается в использовании операции <xref:System.Activities.Statements.Flowchart>. Используйте блок- [схему](../workflow-designer/flowchart-activity-designer.md) , если у вас есть простой поток ветвления или циклическая программа, которую требуется смоделировать диаграмматикалли.

## <a name="using-the-sequence-activity-designer"></a>Использование конструктора действий Sequence
 Чтобы добавить действие <xref:System.Activities.Statements.Sequence>, перетащите конструктор действий **последовательности** из **области элементов** в область [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Чтобы добавить дочернее действие к этому <xref:System.Activities.Statements.Sequence> действию, перетащите другое действие из **панели элементов** и поместите его на треугольник в поле с текстом подсказки "перетащите действие сюда".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Свойства действия Sequence в конструкторе рабочих процессов
 В следующей таблице показаны свойства <xref:System.Activities.Statements.Sequence> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств или в области конструктора.

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.Sequence> в заголовке. Значение по умолчанию - Sequence. Значение можно дополнительно изменить в таблице свойств или напрямую в заголовке конструктора операций.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|

## <a name="see-also"></a>См. также раздел
 [Поток управления](../workflow-designer/control-flow-activity-designers.md) [блок-схемой](../workflow-designer/flowchart-activity-designer.md)