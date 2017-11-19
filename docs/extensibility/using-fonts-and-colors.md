---
title: "Шрифты и цвета | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce64c7cac36319d1e55efb0ddf2216dc218805c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="using-fonts-and-colors"></a>Шрифты и цвета
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Обеспечивает поддержку использования шрифты и цвета для отображения текста.  
  
## <a name="in-this-section"></a>Содержание  
 [Обзор цвет и шрифт](../extensibility/font-and-color-overview.md)  
 Описание параметров шрифта и цвета текста в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Также понятия, категории и отображаемые элементы и описывает, как использовать атрибуты текста в пакеты VSPackage и базового редактора.  
  
 [Получение шрифт и цвет шрифта для текста выделение цветом](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Содержит рекомендации по реализации выделение текста цветом в пакеты VSPackage, управление **категории** отличный от **текстовый редактор**.  
  
 [Доступ к хранимой шрифта и цветов](../extensibility/accessing-stored-font-and-color-settings.md)  
 Объясняет, как текущий цвет шрифта и параметров можно хранить, извлекать и применения.  
  
 [Реализация пользовательских категорий и отображаемые элементы](../extensibility/implementing-custom-categories-and-display-items.md)  
 Описывает основные шаги, с помощью которых можно создать и использовать собственный из окна **отображать элементы** и **категории** для поддержки отображения текста.  
  
 Этот подход требует VSPackage для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейса и связанных интерфейсов.  
  
 [Как: доступ к встроенных шрифтов и цветов](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Описывает, как определить категории с помощью встроенных шрифты и цвета, и инициировать использование системных шрифтов и цветов.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Предоставляет экземпляр `IVsFontAndColorDefaults` или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, который соответствует какой-либо элемент в списке в **Показать параметры для** списка в **шрифты и цвета** страница **Параметры** диалоговое окно.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Включает VSPackage для поддержки IDE **шрифты и цвета** страницы путем определения цвета и шрифты по умолчанию для окна или компонент пользовательского интерфейса.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Предоставляет механизм, с помощью которого пакет VSPackage, который обеспечивает поддержку шрифта и цвета можно указать группу отображаемым элементом - супертипом категорию, представляющее собой объединение двух или более категорий.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Включает пакет VSPackage получить данные шрифта и цвета, либо сохранить в реестре.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Уведомляет пакеты VSPackage, в которых используется шрифт и цвет сведения об изменениях в параметрах шрифтов и цветов.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Предоставляет средства для работы с входными и выходными данными, используемые методы [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **шрифт и цвет** механизм.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Управляет кэшированием параметров шрифта и цвета.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)  
 Описывает, как пакеты VSPackage можно использовать для настройки служб языка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактора.  
  
 [Цветовая маркировка синтаксиса в специализированных редакторах](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries как [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор использует службы языка для реализации Цветовая подсветка синтаксиса.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Описание способов использования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] служб для создания элементов пользовательского интерфейса, которые соответствуют остальной части [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].