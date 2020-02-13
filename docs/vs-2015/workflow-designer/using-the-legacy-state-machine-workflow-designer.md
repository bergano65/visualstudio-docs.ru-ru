---
title: Использование устаревшего конечного автомата конструктор рабочих процессов | Документация Майкрософт
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
ms.openlocfilehash: 77bb2c7abb49dbf6fe973ebc80f8340000e4afbd
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846008"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Использование конструктора рабочих процессов конечного автомата для прежних версий
При создании нового проекта рабочего процесса конечного автомата в [!INCLUDE[vs2010](../includes/vs2010-md.md)], предназначенном для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], можно выбрать шаблон проекта " **приложение-консоль рабочего процесса конечного** автомата" или "устаревший проект **библиотеки рабочих процессов конечного автомата** ". Если выбрать один из этих шаблонов проекта конечного автомата, то конструктор конечного автомата использует пользовательский интерфейс конструктора рабочих процессов прежней версии. Дополнительные сведения о шаблонах проектов устаревших автоматов см. в разделе [как создать консольные приложения для рабочих процессов конечного автомата (прежние версии)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) и [как создать библиотеку рабочих процессов конечного автомата (устаревшая)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Рабочий процесс конечного автомата состоит из набора состояний. Одно состояние обозначается как начальное состояние. Каждое состояние может получить определенный набор событий. В зависимости от события, может быть сделан переход в другое состояние. Рабочий процесс конечного автомата может иметь конечное состояние. При переходе в конечное состояние рабочий процесс завершается.

## <a name="state-machine-designer-views"></a>Представления конструктора конечных автоматов
 Конструктор конечных автоматов - это конструктор свободных форм, что в свою очередь означает, что действия могут свободно перемещаться в рабочей области конструктора. Конструктор конечного автомата имеет два представления: представление *состояний* и представление, *управляемое событиями* .

 В представлении состояния показываются действия, связанные с состоянием, и действия, управляемые событиями, которые могут содержаться в действии, связанном с состоянием. В этом представлении переход из одного состояние в другое представляется линиями, которые исходят из действия, управляемого событием, из одного состояния в другое. Также можно создавать переходы путем рисования линии. Чтобы нарисовать переход, выберите действие, управляемое событием, далее выберите один из маркеров в действии и перетащите его. При этом рисуется линия. Далее эта линия прикрепляется в целевому состоянию с указанием перехода между состояниями.

 Для доступа к представлению, управляемому событием, дважды щелкните действие, управляемое событиями. Появившийся конструктор очень похож на конструктор последовательных рабочих процессов. На панели переходов в верхней части конструктора показана иерархия действий до отображаемого действия, управляемого событиями. Переход назад к представлению состояния можно выполнить по щелчку любого элемента в показанной иерархии. Если в представлении состояния был нарисован переход из одного состояния в другое и если для этого действия отображается представление, управляемое событиями, то к действию, управляемому событием, добавляется действие установки состояния. Если изменить свойства действия установки состояния, то это отражается в представлении состояния.

## <a name="state-machine-workflow-activities"></a>Действия рабочего процесса конечного автомата
 В следующей таблице представлены основные действия, которые используются в конструкторе рабочих процессов конечного автомата.

|Имя панели элементов|Действие|Описание|
|------------------|--------------|-----------------|
|**Состояние**|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|Представляет состояние на компьютере конечного компьютера; может содержать дополнительные действия **StateActivity** . Дополнительные сведения см. [в разделе Использование действия StateActivity](https://msdn2.microsoft.com/library/bb628612.aspx).|
|**SetState**|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|Задает переход к новому состоянию. Дополнительные сведения см. [в разделе Использование действия SetStateActivity](https://msdn2.microsoft.com/library/bb628469.aspx).|
|**StateInitialization**|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|Выполняется при входе в состояние; может содержать другие действия. Дополнительные сведения см. [в разделе Использование действия StateInitialization](https://msdn2.microsoft.com/library/bb675253.aspx).|
|**StateFinalization**|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|Выполняет вложенные операции при закрытии действия [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) . Дополнительные сведения см. [в разделе Использование действия StateFinalizationActivity](https://msdn2.microsoft.com/library/bb675278.aspx).|
|**EventDriven**|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|Используется для состояний, которые начинают выполняться при возникновении внешних событий. Действие **EventDrivenActivity** должно иметь действие, реализующее интерфейс [IEventActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ieventactivity.aspx) в качестве первого дочернего действия. Дополнительные сведения см. [в разделе Использование действия EventDrivenActivity](https://msdn2.microsoft.com/library/bb628466.aspx).|

 Основным компонентом в рабочем процессе конечного автомата является действие [StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) . Поскольку события захватываются в различных точках рабочего процесса конечного автомата, вводятся различные состояния для обработки задач, которые связаны с событиями. В течение времени существования рабочий процесс может выходить и входить в несколько различных состояний. Эти состояния соединяются друг с другом с помощью действия [SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx) .

 При перетаскивании нового **StateActivity** в рабочую область конструктора рабочих процессов можно добавлять [EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx), [StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx), [StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)или дополнительные действия **StateActivity** как дочерние действия.

> [!CAUTION]
> При использовании конструктора рабочих процессов конечного автомата для создания рабочих процессов необходимо отследить структуру рабочего процесса, который вы разрабатываете, с помощью окна "представление **структуры документа** ". Представление структуры рабочего процесса конечного автомата в окне представление **структуры документа** отражает логическую структуру действий в файле разметки рабочего процесса. Физическая структура действий рабочего процесса в том виде, в котором они появляются в рабочей области конструктора, может не отражать логическую структуру действий в файле разметки рабочего процесса.
>
> Чтобы открыть окно " **Структура документа** ", в меню **вид** наведите указатель на пункт **другие окна**, а затем выберите **Структура документа**.

## <a name="see-also"></a>См. также раздел
 [Как создать консольные приложения для рабочих процессов конечного автомата (прежние версии)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) как создать рабочие процессы конечного автомата [(устаревшие) для](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [рабочих процессов](https://msdn2.microsoft.com/library/bb628601.aspx) конечных автоматов с помощью действия [StateActivity](https://msdn2.microsoft.com/library/bb628612.aspx) с помощью действия [StateInitializationActivity](https://msdn2.microsoft.com/library/bb675253.aspx) , используя действие [StateFinalizationActivity](https://msdn2.microsoft.com/library/bb675278.aspx) с действием [SetStateActivity](https://msdn2.microsoft.com/library/bb628469.aspx) с действием [EventDrivenActivity](https://msdn2.microsoft.com/library/bb628466.aspx)
