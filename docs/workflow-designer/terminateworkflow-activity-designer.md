---
title: Конструктор действий конструктор рабочих процессов TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078dfb43b5960580327448627a30eec20297d9f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "76111776"
---
# <a name="terminateworkflow-activity-designer"></a>Конструктор действия TerminateWorkflow

Конструктор действий **TerminateWorkflow** используется для создания и настройки <xref:System.Activities.Statements.TerminateWorkflow> действия.

## <a name="the-terminateworkflow-activity"></a>Действие TerminateWorkflow

Действие <xref:System.Activities.Statements.TerminateWorkflow> прерывает выполнение текущего рабочего процесса.

### <a name="using-the-terminateworkflow-activity-designer"></a>Использование конструктора операций TerminateWorkflow

Конструктор действий **TerminateWorkflow** можно найти в категории **Среда выполнения** **панели элементов**, щелкнув вкладку **область элементов** (также можно выбрать **область элементов** в меню **вид** или CTRL + ALT + X).

Конструктор действий **TerminateWorkflow** можно перетащить из **панели элементов** в область Конструктор рабочих процессов, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.TerminateWorkflow> действие со значением **DisplayName** по умолчанию TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **TerminateWorkflow** или в поле **DisplayName** сетки свойств.

### <a name="the-terminateworkflow-properties"></a>Свойства TerminateWorkflow

В следующей таблице показаны свойства <xref:System.Activities.Statements.TerminateWorkflow> и описано их использование в конструкторе. Эти свойства можно изменять в сетке свойств, а некоторые из них можно редактировать на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.TerminateWorkflow>. Значение по умолчанию - TerminateWorkflow. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Неверно|Исключение, которое будет создано при прерывании рабочего процесса. Задайте это свойство в таблице свойств.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Неверно|Причина, которая объясняет причину прерывания рабочего процесса. Задайте это свойство в таблице свойств.|

## <a name="see-also"></a>См. также раздел

- [Параметры выполнения](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
