---
title: Объекты контекста выбора Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705514"
---
# <a name="selection-context-objects"></a>Объекты контекста выбора
Интегрированная [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среда разработки (IDE) использует глобальный объект контекста выбора для определения того, что должно отображаться в IDE. Каждое окно в IDE может иметь свой собственный объект контекста выбора, отодвинутый в глобальный контекст выбора. IDE обновляет контекст глобального выбора значениями из окна, когда это окно имеет фокус. Для получения дополнительной информации смотрите [отзывы пользователей](../../extensibility/internals/feedback-to-the-user.md).

 Каждая оконная рама или сайт <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>в IDE имеет службу под названием . Объект, созданный vsPackage, который находится в оконной `QueryService` раме, должен вызвать метод, чтобы получить указатель на <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс.

 Окна кадра могут удерживать часть информации о контексте выбора от распространения в глобальном контексте выбора при их начале. Эта возможность полезна для окон инструментов, которые, возможно, придется начинать с пустого выбора.

 Изменение глобального контекста выбора вызывает события, которые могут контролировать VSPackages. VSPackages может выполнять следующие `IVsTrackSelectionEx` задачи <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> путем реализации и интерфейсов:

- Обновление действующего файла в иерархии.

- Мониторинг изменений определенных типов элементов. Например, если ваш VSPackage использует специальное окно **Свойств,** вы можете отслеживать изменения в окне **активных свойств** и перезапустить ваше окно, когда это необходимо.

  Следующая последовательность показывает типичный ход отслеживания отбора.

1. IDE извлекает контекст выбора из недавно открытого окна и помещает его в контекст глобального выбора. Если контекст выбора использует HIERARCHY_DONTPROPAGATE или SELCONTAINER_DONTPROPAGATE, эта информация не распространяется в глобальном контексте. Для получения дополнительной информации смотрите [отзывы пользователей](../../extensibility/internals/feedback-to-the-user.md).

2. Уведомления события транслируются на любой VSPackage, которые просили их.

3. VSPackage действует на события, которые он получает, выполняя такие действия, как обновление иерархии, реактивация инструмента или другие аналогичные задачи.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Выбор и актуальность в интегрированной среде разработки](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Типы проектов](../../extensibility/internals/project-types.md)
