---
title: Объекты контекста выбора | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a74e86cb050dcbc1262bd3bf060f76b8bbc38f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569198"
---
# <a name="selection-context-objects"></a>Объекты контекста выбора
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [объекты контекста выбора](https://docs.microsoft.com/visualstudio/extensibility/internals/selection-context-objects).  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Интегрированной среды разработки (IDE) использует объект контекста глобального выделения для определения того, что должно быть отображено в интегрированной среде разработки. Каждое окно в интегрированной среде разработки может иметь свой собственный объект контекста выбора, в контексте глобального выделения. При этого окна имеет фокус, со значениями из окна интегрированной среды разработки обновляет контекст глобального выделения. Дополнительные сведения см. в разделе [обратной связи с пользователем](../../extensibility/internals/feedback-to-the-user.md).  
  
 Каждый фрейм окна или узла в интегрированной среде разработки имеет службу, именуемую <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Объект, созданный VSPackage, размещаемым в фрейме окна необходимо вызвать `QueryService` метод, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс.  
  
 Окна фрейма можно сохранить часть их сведения о контексте выбора распространяться контексте глобального выделения при запуске. Эта возможность полезна для окон инструментов, возможно, потребуется начать с пустой выборке.  
  
 Изменение глобального выделения контекстные триггеров события, которые можно отслеживать пакеты VSPackage. Пакеты VSPackage могут выполнять следующие задачи по реализации `IVsTrackSelectionEx` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> интерфейсы:  
  
-   Обновление файла в иерархии.  
  
-   Отслеживание изменений для определенных типов элементов. Например, если VSPackage использует специальный **свойства** окно, можно отслеживать изменения в активном **свойства** окно и перезапустите вам при необходимости.  
  
 Следующая последовательность действий показывает типичный ход отслеживание выделения.  
  
1.  Интегрированная среда разработки получает контекст выбора из только что открытого окна и помещает его в контексте глобального выделения. Если контекст выбора с HIERARCHY_DONTPROPAGATE или SELCONTAINER_DONTPROPAGATE, эти сведения не распространяется на глобальном контексте. Дополнительные сведения см. в разделе [обратной связи с пользователем](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  События уведомления отправляются любой пакет VSPackage, который их запросил.  
  
3.  Пакет VSPackage, выступает на события, которые оно получает, выполняя действия, такие как обновление иерархии, повторная активация средство или других подобных целей.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Типы проектов](../../extensibility/internals/project-types.md)

