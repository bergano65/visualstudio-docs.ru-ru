---
title: "Объекты контекста выбора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3fa5093ee38c364a4766160f8642755bc0b2a23f
ms.lasthandoff: 02/22/2017

---
# <a name="selection-context-objects"></a>Выбор контекста объектов
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) использует объект контекста глобального выделения для определения того, что должно быть отображено в Интегрированной среде разработки. Каждое окно в Интегрированной среде разработки может иметь свой собственный объект контекста выбора помещено в контекст глобального выделения. Контекст глобального выделения обновляет интегрированной среды разработки со значениями из окна при это окно находится в фокусе. Дополнительные сведения см. в разделе [обратной связи с пользователем](../../extensibility/internals/feedback-to-the-user.md).  
  
 Каждая рамка окна или узла в Интегрированной среде разработки имеет службу, именуемую <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.</xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Объект, созданный VSPackage, находящегося в рамке окна необходимо вызвать `QueryService` метод, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>  
  
 Окна фрейма можно хранить частей их Выбор сведений о контексте распространению контекст глобального выделения при запуске. Эта возможность полезна для окон инструментов, возможно, придется начать с пустой выборке.  
  
 Изменение события триггеров глобального выделения контекста, которые можно отслеживать пакеты VSPackage. Пакеты VSPackage можно выполнять следующие задачи по реализации `IVsTrackSelectionEx` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>интерфейсов:</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>  
  
-   Обновление текущего активного файла в иерархии.  
  
-   Отслеживание изменений для определенных типов элементов. Например, если VSPackage использует специальный **свойства** окна, можно отслеживать изменения в активном **свойства** окно и перезапустите вас при необходимости.  
  
 Следующая последовательность действий показывает типичный ход Выбор отслеживания.  
  
1.  IDE получает контекст выделения с только что открытого окна и помещает его в контексте глобального выделения. Если контекст выделения использует HIERARCHY_DONTPROPAGATE или SELCONTAINER_DONTPROPAGATE, эти сведения не распространяется на глобальном контексте. Дополнительные сведения см. в разделе [обратной связи с пользователем](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  События уведомления отправляются для любого VSPackage, который их запросил.  
  
3.  VSPackage обрабатывает события, получаемые им, выполнив действия, такие как обновление иерархии, повторная активация средство или других подобных задач.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Выбор и денежные единицы в Интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Типы проектов](../../extensibility/internals/project-types.md)
