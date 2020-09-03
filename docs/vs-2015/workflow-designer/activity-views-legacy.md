---
title: Представления действий (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851480"
---
# <a name="activity-views-legacy"></a>Представления действий (для прежних версий)
Для многих предоставляемых средой [!INCLUDE[wf](../includes/wf-md.md)] действий, из которых составляются рабочие процессы, в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий доступно несколько представлений конструкторов. При перетаскивании конструктора действий из **области элементов** в область конструктора, а затем при каждом выборе действия можно переключаться между различными представлениями конструктора, используя меню **рабочего процесса** или щелкнув правой кнопкой мыши выбранное действие. Также при перемещении указателя над именем выбранного действия, появляется раскрывающийся набор вкладок, который можно использовать для переключения между различными представлениями.

 Каждое действие имеет по крайней мере одно представление; Это представление по умолчанию, отображаемое при перетаскивании конструктора действий из **панели элементов** в область конструктора. Это представление действия по умолчанию доступно в виде параметра **View [тип действия]** в меню и на вкладке, например в поле **параллельное**представление. Большая часть этих действий имеет дополнительные представления, различные действия могут иметь различные представления. Например, действие [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) имеет представление компенсации, а действие [евенсандлингскопеактивити](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) — представление событий. Многие из действий, поступающих с Windows Workflow Foundation, имеют **обработчики просмотра отмены** и представлений **ошибок View** , чтобы просмотреть [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) и [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) , связанные с ними.

 В следующей таблице перечислены имена и описание каждого представления.

|Параметры меню/вкладок|Описание|
|----------------------|-----------------|
|**Просмотр [тип действия]**|Выберите эту команду меню (вкладки) для просмотра графического представления по умолчанию выбранного действия.|
|**Просмотр обработчика отмены**|Выберите это меню или режим вкладки, чтобы просмотреть [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) , связанный с выбранным действием.|
|**Просмотр обработчика ошибок**|Выберите это меню или режим вкладки, чтобы просмотреть [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) , связанный с выбранным действием.|
|**Просмотр обработчика компенсаций**|Выберите это меню или режим вкладки, чтобы просмотреть [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) , связанный с выбранным [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx).|
|**Просмотр обработчика событий**|Выберите это меню или режим вкладки, чтобы просмотреть [евенсандлерсактивити](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) , связанный с выбранным [евенсандлингскопеактивити](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx).|

 Сведения о схожих представлениях см. в разделе [последовательные представления рабочего процесса (прежние версии)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>См. также:
 Устаревшие представления рабочего процесса с последовательными [действиями рабочих процессов](../workflow-designer/legacy-workflow-activities.md) [(прежние версии)](../workflow-designer/sequential-workflow-views-legacy.md)
