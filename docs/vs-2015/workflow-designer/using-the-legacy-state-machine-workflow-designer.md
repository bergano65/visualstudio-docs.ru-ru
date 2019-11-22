---
title: Using the Legacy State Machine Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bab07b8ba0b71bd880135518ff9ff5fc697d54c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302810"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Использование конструктора рабочих процессов конечного автомата для прежних версий
When you are creating a new state machine workflow project in [!INCLUDE[vs2010](../includes/vs2010-md.md)] that targets either the [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] or the [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], you can choose to use either the **State Machine Workflow Console Application** or the **State Machine Workflow Library** legacy project template. Если выбрать один из этих шаблонов проекта конечного автомата, то конструктор конечного автомата использует пользовательский интерфейс конструктора рабочих процессов прежней версии. For information about the legacy state machine project templates, see [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) and [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Рабочий процесс конечного автомата состоит из набора состояний. Одно состояние обозначается как начальное состояние. Каждое состояние может получить определенный набор событий. В зависимости от события, может быть сделан переход в другое состояние. Рабочий процесс конечного автомата может иметь конечное состояние. При переходе в конечное состояние рабочий процесс завершается.

## <a name="state-machine-designer-views"></a>Представления конструктора конечных автоматов
 Конструктор конечных автоматов - это конструктор свободных форм, что в свою очередь означает, что действия могут свободно перемещаться в рабочей области конструктора. The state machine designer has two views: *state* view and *event-driven* view.

 В представлении состояния показываются действия, связанные с состоянием, и действия, управляемые событиями, которые могут содержаться в действии, связанном с состоянием. В этом представлении переход из одного состояние в другое представляется линиями, которые исходят из действия, управляемого событием, из одного состояния в другое. Также можно создавать переходы путем рисования линии. Чтобы нарисовать переход, выберите действие, управляемое событием, далее выберите один из маркеров в действии и перетащите его. При этом рисуется линия. Далее эта линия прикрепляется в целевому состоянию с указанием перехода между состояниями.

 Для доступа к представлению, управляемому событием, дважды щелкните действие, управляемое событиями. Появившийся конструктор очень похож на конструктор последовательных рабочих процессов. На панели переходов в верхней части конструктора показана иерархия действий до отображаемого действия, управляемого событиями. Переход назад к представлению состояния можно выполнить по щелчку любого элемента в показанной иерархии. Если в представлении состояния был нарисован переход из одного состояния в другое и если для этого действия отображается представление, управляемое событиями, то к действию, управляемому событием, добавляется действие установки состояния. Если изменить свойства действия установки состояния, то это отражается в представлении состояния.

## <a name="state-machine-workflow-activities"></a>Действия рабочего процесса конечного автомата
 В следующей таблице представлены основные действия, которые используются в конструкторе рабочих процессов конечного автомата.

|Имя панели элементов|Действие|Описание|
|------------------|--------------|-----------------|
|**Состояние**|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Represents a state in a state machine; may contain additional **StateActivity** activities. For more information, see [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083).|
|**SetState**|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Задает переход к новому состоянию. For more information, see [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Выполняется при входе в состояние; может содержать другие действия. For more information, see [Using the StateInitialization Activity](https://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Executes contained activities when leaving a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. For more information, see [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Используется для состояний, которые начинают выполняться при возникновении внешних событий. The **EventDrivenActivity** activity must have an activity that implements the [IEventActivity](https://go.microsoft.com/fwlink?LinkID=65032) interface as the first child activity. For more information, see [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068).|

 The main component in a state machine workflow is the [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity. Поскольку события захватываются в различных точках рабочего процесса конечного автомата, вводятся различные состояния для обработки задач, которые связаны с событиями. В течение времени существования рабочий процесс может выходить и входить в несколько различных состояний. These states connect to each other by using the [SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041) activity.

 When you drag a new **StateActivity** onto the workflow design surface, you can add [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043), or additional **StateActivity** activities as child activities.

> [!CAUTION]
> When you use the state machine workflow designer to create workflows, you must monitor the structure of the workflow you are designing with the **Document Outline** view window. The view of the structure of the state machine workflow in the **Document Outline** view window mirrors the logical layout of the activities in the workflow markup file. Физическая структура действий рабочего процесса в том виде, в котором они появляются в рабочей области конструктора, может не отражать логическую структуру действий в файле разметки рабочего процесса.
>
> To open the **Document Outline** window, on the **View** menu, point to **Other Windows**, and then select **Document Outline**.

## <a name="see-also"></a>См. также раздел
 [How to: Create State Machine Workflow Console Applications (Legacy)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) [How to: Create a State Machine Workflow Library (Legacy)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [State Machine Workflows](https://go.microsoft.com/fwlink?LinkID=65016) [Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083) [Using the StateInitializationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65006) [Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008) [Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082) [Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068)