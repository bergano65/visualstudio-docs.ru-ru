---
title: Представления действий (для прежних версий) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ef7aaa042ea358ecdf3d45b6ee75dd14cf117a01
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563658"
---
# <a name="activity-views-legacy"></a>Представления действий (для прежних версий)
Для многих предоставляемых средой [!INCLUDE[wf](../includes/wf-md.md)] действий, из которых составляются рабочие процессы, в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий доступно несколько представлений конструкторов. При перетаскивании конструктора действия из **элементов** в область конструктора и, соответственно всякий раз при выборе действия, можно переключаться между различными представлениями конструктора с помощью **рабочего процесса**меню или щелкнув правой кнопкой мыши выбранное действие. Также при перемещении указателя над именем выбранного действия, появляется раскрывающийся набор вкладок, который можно использовать для переключения между различными представлениями.  
  
 Каждое действие имеет хотя бы одно представление; Это представление по умолчанию, отображаемое при перетаскивании конструктора действия из **элементов** в область конструктора. Это представление по умолчанию доступен в виде **Просмотр [тип действия]** параметр в меню и на вкладке, например, **Просмотр параллельный**. Большая часть этих действий имеет дополнительные представления, различные действия могут иметь различные представления. Например [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) действие имеет представление компенсации и [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) действие имеет событий представления. Многие из действий, поставляемых с Windows Workflow Foundation имеют **Просмотр обработчика отмены** и **Просмотр ошибок** представления к представлению конструктора [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) и [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) связанных с ними.  
  
 В следующей таблице перечислены имена и описание каждого представления.  
  
|Параметры меню/вкладок|Описание|  
|----------------------|-----------------|  
|**Просмотр [тип действия]**|Выберите эту команду меню (вкладки) для просмотра графического представления по умолчанию выбранного действия.|  
|**Просмотр обработчика отмены**|Этот параметр меню или вкладки представления [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) связанные с выбранным действием.|  
|**Просмотр обработчика ошибок**|Этот параметр меню или вкладки представления [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) связанные с выбранным действием.|  
|**Просмотр обработчика компенсаций**|Этот параметр меню или вкладки представления [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) связанного с выбранным [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Просмотр обработчика событий**|Этот параметр меню или вкладки представления [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) связанного с выбранным [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Сведения о похожих представлениях см. в разделе [представления последовательных рабочих процессов (для прежних версий)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>См. также  
 [Действия рабочего процесса прежних версий](../workflow-designer/legacy-workflow-activities.md)   
 [Представления последовательных рабочих процессов (для прежних версий)](../workflow-designer/sequential-workflow-views-legacy.md)