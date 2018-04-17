---
title: Представления действий (для прежних версий) | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2cc053be2f9d11a9a1f3cd48c6c9d24e366410c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="activity-views-legacy"></a>Представления действий (для прежних версий)
Многие действия, предоставляемые [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], из которых составляются рабочие процессы, имеет несколько представлений конструкторов в конструкторе рабочих процессов прежних версий Windows. При перетаскивании конструктора действий из **элементов** в область конструктора и, соответственно всякий раз при выборе действия можно переключаться между различными представлениями конструктора с помощью **рабочего процесса**меню или щелкнув правой кнопкой мыши выбранное действие. Также при перемещении указателя над именем выбранного действия, появляется раскрывающийся набор вкладок, который можно использовать для переключения между различными представлениями.

 Каждое действие имеет хотя бы одно представление; Это представление по умолчанию, отображаемое при перетаскивании конструктора действий из **элементов** на поверхность разработки. Это представление по умолчанию доступен в виде **Просмотр [тип действия]** параметр в меню и на вкладке, например, **Просмотр параллельный**. Большая часть этих действий имеет дополнительные представления, различные действия могут иметь различные представления. Например [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) имеет представление компенсации и [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) действие имеет событий представления. Многие из действий, поставляемых с Windows Workflow Foundation имеют **Просмотр обработчика отмены** и **представление ошибки** создать представления для представления [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) и [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) связанные с ними.

 В следующей таблице перечислены имена и описание каждого представления.

|Параметры меню/вкладок|Описание|
|----------------------|-----------------|
|**Просмотр [тип действия]**|Выберите эту команду меню (вкладки) для просмотра графического представления по умолчанию выбранного действия.|
|**Просмотр обработчика отмены**|Этот параметр меню или вкладку представления [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) связанные с выбранным действием.|
|**Просмотр обработчика ошибок**|Этот параметр меню или вкладку представления [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) связанные с выбранным действием.|
|**Просмотр обработчика компенсаций**|Этот параметр меню или вкладку представления [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) связанного с выбранным [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|
|**Просмотр обработчика событий**|Этот параметр меню или вкладку представления [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) связанного с выбранным [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|

 Сведения о сходные представления см. в разделе [представления последовательных рабочих процессов (для прежних версий)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>См. также

- [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)
- [Представления последовательных рабочих процессов (для прежних версий)](../workflow-designer/sequential-workflow-views-legacy.md)