---
title: Объекты контекста выделения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e1a43997d56f8d89f194fb83d20c1f160378873
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187435"
---
# <a name="selection-context-objects"></a>Объекты контекста выбора
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Интегрированная среда разработки (IDE) использует объект контекста глобального выделения, чтобы определить, что должно отображаться в интегрированной среде разработки. Каждое окно в интегрированной среде разработки может иметь собственный объект контекста выбора, отправленный в глобальный контекст выбора. Интегрированная среда разработки обновляет глобальный контекст выделения значениями из окна, когда это окно находится в фокусе. Дополнительные сведения см. в статье [отзыв пользователю](../../extensibility/internals/feedback-to-the-user.md).  
  
 Для каждого фрейма окна или сайта в интегрированной среде разработки имеется служба с именем <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Объект, созданный пакетом VSPackage, который находится в рамке окна, должен вызывать `QueryService` метод для получения указателя на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс.  
  
 Окна фрейма могут соносить фрагменты сведений о контексте выбора из распространения в глобальный контекст выбора при запуске. Эта возможность полезна для окон инструментов, которые, возможно, придется начать с пустого выделения.  
  
 Изменение контекста глобального выделения активирует события, которые могут отслеживать пакеты VSPackage. Пакеты VSPackage могут выполнять следующие задачи путем реализации `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> интерфейсов и:  
  
- Обновить текущий активный файл в иерархии.  
  
- Отслеживание изменений некоторых типов элементов. Например, если пакет VSPackage использует специальное окно **свойств** , вы можете отслеживать изменения в окне "активные **свойства** " и перезапускать его при необходимости.  
  
  В следующей последовательности показан типичный способ отслеживания выбора.  
  
1. Интегрированная среда разработки извлекает контекст выбора из вновь открытого окна и помещает его в глобальный контекст выбора. Если контекст выбора использует HIERARCHY_DONTPROPAGATE или SELCONTAINER_DONTPROPAGATE, эти сведения не распространяются в глобальный контекст. Дополнительные сведения см. в статье [отзыв пользователю](../../extensibility/internals/feedback-to-the-user.md).  
  
2. События уведомления передаются в любой пакет VSPackage, который запросил их.  
  
3. Пакет VSPackage работает с получаемыми событиями, выполняя такие действия, как обновление иерархии, повторная активация средства или выполнение других аналогичных задач.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Выбор и валюта в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Типы проектов](../../extensibility/internals/project-types.md)
