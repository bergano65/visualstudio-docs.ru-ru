---
title: С помощью шрифты и цвета | Документация Майкрософт
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
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6db4f030a3367a5fd2fb449b3515643fe6cd6033
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558702"
---
# <a name="using-fonts-and-colors"></a>С помощью шрифтов и цветов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [использование шрифтов и цветов](https://docs.microsoft.com/visualstudio/extensibility/using-fonts-and-colors).  
  
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Обеспечивает поддержку использования шрифты и цвета для отображения текста.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Общие сведения о шрифтах и цветах](../extensibility/font-and-color-overview.md)  
 Обсуждаются параметры шрифта и цвета текста в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среды разработки (IDE). Также понятия, категории и отображаемые элементы и описывается, как использовать атрибуты текста в пакеты VSPackage и базовым редактором.  
  
 [Получение сведений о шрифте и цвете для цветового выделения текста](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Содержит рекомендации по реализации цветовое выделение текста в пакеты VSPackage, управление **категории** отличное от **текстовый редактор**.  
  
 [Доступ к хранимым параметрам шрифтов и цветов](../extensibility/accessing-stored-font-and-color-settings.md)  
 Объясняет, как текущего шрифта и цвета параметры можно хранить, извлекать и применены.  
  
 [Реализация пользовательских категорий и отображаемых элементов](../extensibility/implementing-custom-categories-and-display-items.md)  
 Описывает основные шаги, которые можно создать и использовать свой собственный из окна **отображать элементы** и **категории** для поддержки отображения текста.  
  
 Этот подход требует VSPackage для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс и соответствующие интерфейсы.  
  
 [Практическое руководство. Доступ к встроенным шрифтам и цветовой схеме](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Описывает, как определить категорию с помощью встроенных шрифты и цвета, и начала работы для системных шрифтов и цветов.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Предоставляет экземпляр `IVsFontAndColorDefaults` или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, соответствующий элемент, указанный в **Показать параметры для** в списке **шрифты и цвета** странице **Параметры** диалоговое окно.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Разрешает VSPackage осуществлять поддержку интегрированной среды разработки **шрифты и цвета** страницы путем определения по умолчанию шрифты и цвета для окна или компонент пользовательского интерфейса.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Предоставляет механизм, по которому пакет VSPackage, который обеспечивает поддержку шрифтов и цветов можно указать группу элементов отображения — суперкатегорию, которая представляет объединение двух или более категорий.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Позволяет VSPackage извлекать данные шрифта и цвета или сохраните его в реестр.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Уведомляет VSPackages, в которых используется данные шрифта и цвета об изменениях в параметры шрифта и цвета.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Предоставляет средства для работы с входных и выходных данных, который используется с помощью методов класса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **шрифта и цвета** механизм.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Контролирует кэширование параметров шрифта и цвета.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)  
 Описывает, как пакеты VSPackages могут использовать службы языка для настройки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] редактора.  
  
 [Цветовая маркировка синтаксиса в специализированных редакторах](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries как [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] редактор использует языковые службы для реализации Цветовая подсветка синтаксиса.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Содержит сведения об использовании [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] служб для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

