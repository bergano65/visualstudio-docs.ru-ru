---
title: Конструктор рабочих процессов - конструктора операций TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5dfd7438a14f0bcbedcf5cdc5add78020604c355
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975563"
---
# <a name="terminateworkflow-activity-designer"></a>Конструктор действия TerminateWorkflow

**TerminateWorkflow** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.TerminateWorkflow> действия.

## <a name="the-terminateworkflow-activity"></a>Действие TerminateWorkflow

Действие <xref:System.Activities.Statements.TerminateWorkflow> прерывает выполнение текущего рабочего процесса.

### <a name="using-the-terminateworkflow-activity-designer"></a>Использование конструктора операций TerminateWorkflow

**TerminateWorkflow** конструктора действий можно найти в **среды выполнения** категории **элементов**, который нажав **элементов** вкладка (либо выберите **элементов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

**TerminateWorkflow** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.TerminateWorkflow> действия по умолчанию **DisplayName** для TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A> Можно изменить в заголовке **TerminateWorkflow** конструктора или в **DisplayName** поле сетки свойств.

### <a name="the-terminateworkflow-properties"></a>Свойства TerminateWorkflow

В следующей таблице показаны свойства <xref:System.Activities.Statements.TerminateWorkflow> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, и некоторые из них можно изменить на поверхности конструктора рабочих процессов.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.TerminateWorkflow>. Значение по умолчанию - TerminateWorkflow. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Исключение, которое будет создано при прерывании рабочего процесса. Задайте это свойство в таблице свойств.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Причина, которая объясняет причину прерывания рабочего процесса. Задайте это свойство в таблице свойств.|

## <a name="see-also"></a>См. также

- [Среда выполнения](../workflow-designer/runtime-activity-designers.md)
- [Сохранение](../workflow-designer/persist-activity-designer.md)