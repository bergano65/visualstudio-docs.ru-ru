---
title: "Объекты контекста выбора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d97dd10661beb5acb28b464a8bc0d88ba5946924
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="selection-context-objects"></a>Объекты контекста выбора
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) использует объект контекста глобального выделения для определения того, что должно быть отображено в Интегрированной среде разработки. Каждое окно Интегрированной среды разработки может иметь свой собственный объект контекста выбора, помещаются в контекст глобального выделения. При это окно находится в фокусе, со значениями из окна интегрированной среды разработки обновляет контекст глобального выделения. Дополнительные сведения см. в разделе [отзывы пользователю](../../extensibility/internals/feedback-to-the-user.md).  
  
 Каждая рамка окна или узла в Интегрированной среде разработки имеет службу под названием <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Объект, созданный VSPackage, размещаемым в фрейме окна необходимо вызвать `QueryService` метод, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейса.  
  
 Окна фрейма можно сохранить часть свои сведения о контексте выбор из распространяется на контекст глобального выделения при запуске. Эта возможность полезна для окон инструментов, которые может потребоваться начать с пустой выборке.  
  
 Изменение триггеров событий глобального выделения контекста, можно отслеживать пакеты VSPackage. Пакеты VSPackage могут выполнять следующие задачи по реализации `IVsTrackSelectionEx` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> интерфейсы:  
  
-   Обновите активный файл в иерархии.  
  
-   Отслеживать изменения в определенных типов элементов. Например, если пакет VSPackage использует специальный **свойства** окна, можно отслеживать изменения в активном **свойства** окно и перезапустите вам при необходимости.  
  
 Следующая последовательность действий показывает типичный ход отслеживание выделения.  
  
1.  Получает контекст выбора из только что открытого окна интегрированной среды разработки и помещает его в контекст глобального выделения. Если контекст выбора использует HIERARCHY_DONTPROPAGATE или SELCONTAINER_DONTPROPAGATE, эти сведения не отражается в глобальном контексте. Дополнительные сведения см. в разделе [отзывы пользователю](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  События уведомления рассылаются любой пакет VSPackage, который запросил их.  
  
3.  Пакет VSPackage обрабатывает события, получаемые им, выполнив действия, такие как обновление иерархии, повторная активация средство или других подобных задач.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Выбор и денежные единицы в Интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Типы проектов](../../extensibility/internals/project-types.md)