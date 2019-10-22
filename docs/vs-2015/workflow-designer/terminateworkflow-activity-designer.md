---
title: Конструктор действий TerminateWorkflow | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c204c14818a9c6e6fb0a46e6234b550838f3b1a4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607097"
---
# <a name="terminateworkflow-activity-designer"></a>Конструктор действия TerminateWorkflow
Конструктор действий **TerminateWorkflow** используется для создания и настройки действия <xref:System.Activities.Statements.TerminateWorkflow>.

## <a name="the-terminateworkflow-activity"></a>Действие TerminateWorkflow
 Действие <xref:System.Activities.Statements.TerminateWorkflow> прерывает выполнение текущего рабочего процесса.

### <a name="using-the-terminateworkflow-activity-designer"></a>Использование конструктора операций TerminateWorkflow
 Конструктор действий **TerminateWorkflow** можно найти в категории **Среда выполнения** **панели элементов**, щелкнув вкладку **область элементов** (также можно выбрать **область элементов** в меню **вид** или CTRL + ALT + X.)

 Конструктор действий **TerminateWorkflow** можно перетащить из **панели элементов** в область [!INCLUDE[wfd2](../includes/wfd2-md.md)], где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается действие <xref:System.Activities.Statements.TerminateWorkflow> со значением **DisplayName** по умолчанию TerminateWorkflow. @No__t_0 можно изменить в заголовке конструктора действий **TerminateWorkflow** или в поле **DisplayName** сетки свойств.

### <a name="the-terminateworkflow-properties"></a>Свойства TerminateWorkflow
 В следующей таблице показаны свойства <xref:System.Activities.Statements.TerminateWorkflow> и описано их использование в конструкторе. Эти свойства можно изменить в таблице свойств, а некоторые из них можно изменить в области [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Имя свойства|Обязательное значение|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.TerminateWorkflow>. Значение по умолчанию - TerminateWorkflow. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Исключение, которое будет создано при прерывании рабочего процесса. Задайте это свойство в таблице свойств.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Причина, которая объясняет причину прерывания рабочего процесса. Задайте это свойство в таблице свойств.|

## <a name="see-also"></a>См. также раздел
 [Хранимая](../workflow-designer/persist-activity-designer.md) [Среда выполнения](../workflow-designer/runtime-activity-designers.md)