---
title: С помощью шрифты и цвета | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96abe68838d028c5de9d6d9418e94ba5b46c0f76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432307"
---
# <a name="using-fonts-and-colors"></a>С помощью шрифтов и цветов
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Обеспечивает поддержку использования шрифты и цвета для отображения текста.

## <a name="in-this-section"></a>В этом разделе
- [Шрифт и цвет Обзор](../extensibility/font-and-color-overview.md) рассматриваются параметры шрифта и цвета текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Также понятия, категории и отображаемые элементы и описывается, как использовать атрибуты текста в пакеты VSPackage и базовым редактором.

- [Получение шрифт и цвет шрифта для текста цветом](../extensibility/getting-font-and-color-information-for-text-colorization.md) представлены рекомендации по реализации цветовое выделение текста в пакеты VSPackage, управление **категории** отличное от **текстовый редактор**.

- [Доступ к хранящихся шрифтов и цветов](../extensibility/accessing-stored-font-and-color-settings.md) Explains как могут храниться текущие параметры шрифта и цвета, получение и применение.

- [Реализация пользовательских категорий и отображать элементы](../extensibility/implementing-custom-categories-and-display-items.md) описывает основные шаги, которые можно создать и использовать свой собственный из окна **отображать элементы** и **категории** для поддержки отображения текста.

 Этот подход требует VSPackage для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс и соответствующие интерфейсы.

- [Практическое руководство. Доступ к встроенной шрифтов и цветовой схемы](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md) описывает, как определить категорию с помощью встроенных шрифты и цвета, и начала работы для системных шрифтов и цветов.

## <a name="reference"></a>Ссылка
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Предоставляет экземпляр `IVsFontAndColorDefaults` или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, соответствующий элемент, указанный в **Показать параметры для** в списке **шрифты и цвета** странице **Параметры** диалоговое окно.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Разрешает VSPackage осуществлять поддержку интегрированной среды разработки **шрифты и цвета** страницы путем определения по умолчанию шрифты и цвета для окна или компонент пользовательского интерфейса.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Предоставляет механизм, по которому пакет VSPackage, который обеспечивает поддержку шрифтов и цветов можно указать группу элементов отображения — суперкатегорию, которая представляет объединение двух или более категорий.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Позволяет VSPackage извлекать данные шрифта и цвета или сохраните его в реестр.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Уведомляет VSPackages, в которых используется данные шрифта и цвета об изменениях в параметры шрифта и цвета.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> Предоставляет средства для работы с входных и выходных данных, который используется с помощью методов класса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **шрифта и цвета** механизм.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Контролирует кэширование параметров шрифта и цвета.

## <a name="related-sections"></a>Связанные разделы
- [Разработка языковой службы прежних](../extensibility/internals/developing-a-legacy-language-service.md) рассматриваются как пакеты VSPackages могут использовать службы языка для настройки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора.

- [Цветовая маркировка синтаксиса в пользовательских редакторов](../extensibility/syntax-coloring-in-custom-editors.md) Descries как [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор использует языковые службы для реализации Цветовая подсветка синтаксиса.

- [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md) содержит сведения об использовании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] служб для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].