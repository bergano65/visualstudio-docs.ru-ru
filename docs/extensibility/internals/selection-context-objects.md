---
title: Объекты контекста выделения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc4f0aad4dd3f28f28259d0ca439a0cda1a520d9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723916"
---
# <a name="selection-context-objects"></a>Объекты контекста выбора
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) для определения того, что должно отображаться в ИНТЕГРИРОВАНной среде разработки, используется объект контекста глобального выделения. Каждое окно в интегрированной среде разработки может иметь собственный объект контекста выбора, отправленный в глобальный контекст выбора. Интегрированная среда разработки обновляет глобальный контекст выделения значениями из окна, когда это окно находится в фокусе. Дополнительные сведения см. в статье [отзыв пользователю](../../extensibility/internals/feedback-to-the-user.md).

 Каждый фрейм окна или сайт в интегрированной среде разработки имеет службу, именуемую <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Объект, созданный пакетом VSPackage, который находится в рамке окна, должен вызывать метод `QueryService` для получения указателя на интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

 Окна фрейма могут соносить фрагменты сведений о контексте выбора из распространения в глобальный контекст выбора при запуске. Эта возможность полезна для окон инструментов, которые, возможно, придется начать с пустого выделения.

 Изменение контекста глобального выделения активирует события, которые могут отслеживать пакеты VSPackage. Пакеты VSPackage могут выполнять следующие задачи путем реализации `IVsTrackSelectionEx` и <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> интерфейсов:

- Обновить текущий активный файл в иерархии.

- Отслеживание изменений некоторых типов элементов. Например, если пакет VSPackage использует специальное окно **свойств** , вы можете отслеживать изменения в окне "активные **свойства** " и перезапускать его при необходимости.

  В следующей последовательности показан типичный способ отслеживания выбора.

1. Интегрированная среда разработки извлекает контекст выбора из вновь открытого окна и помещает его в глобальный контекст выбора. Если контекст выбора использует HIERARCHY_DONTPROPAGATE или SELCONTAINER_DONTPROPAGATE, эти сведения не распространяются в глобальный контекст. Дополнительные сведения см. в статье [отзыв пользователю](../../extensibility/internals/feedback-to-the-user.md).

2. События уведомления передаются в любой пакет VSPackage, который запросил их.

3. Пакет VSPackage работает с получаемыми событиями, выполняя такие действия, как обновление иерархии, повторная активация средства или выполнение других аналогичных задач.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Типы проектов](../../extensibility/internals/project-types.md)