---
title: Использование шрифтов и цветов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177225"
---
# <a name="using-fonts-and-colors"></a>Использование шрифтов и цветов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Поддерживает использование шрифтов и цветов для вывода текста.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о шрифтах и цветах](../extensibility/font-and-color-overview.md)  
 Обсуждаются параметры шрифта и цвета текста в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среде разработки (IDE). Также содержит основные понятия категорий и отображаемых элементов и описывает, как пакеты VSPackage и основной редактор используют текстовые атрибуты.  
  
 [Получение сведений о шрифте и цвете для цветового выделения текста](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Содержит рекомендации по реализации цветовой цветопередачи в пакетах VSPackage, которые управляют **категориями** , отличными от **текстового редактора**.  
  
 [Доступ к хранимым параметрам шрифтов и цветов](../extensibility/accessing-stored-font-and-color-settings.md)  
 Объясняет, как можно сохранять, извлекать и применять текущие параметры шрифта и цвета.  
  
 [Реализация пользовательских категорий и отображаемых элементов](../extensibility/implementing-custom-categories-and-display-items.md)  
 Описывает основные шаги, по которым окно может создавать и использовать собственные **Отображаемые элементы** и **категории** для поддержки отображаемого текста.  
  
 Этот подход требует, чтобы пакет VSPackage реализовал <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс и связанные интерфейсы.  
  
 [Практическое руководство. Доступ к встроенным шрифтам и цветовой схеме](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Описывает, как определить и зарегистрировать категорию с помощью встроенных шрифтов и цветов, а также инициировать использование предоставленных системой шрифтов и цветов.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Предоставляет экземпляр `IVsFontAndColorDefaults` или <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, соответствующий определенному элементу, указанному в списке **Показывать параметры для** в диалоговом окне **Параметры** на странице **шрифты и цвета** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Позволяет пакету VSPackage поддерживать страницу « **шрифты и цвета** » IDE, определяя шрифты и цвета по умолчанию для окна или компонента пользовательского интерфейса.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Предоставляет механизм, с помощью которого пакет VSPackage, обеспечивающий поддержку шрифта и цвета, может указать группу отображаемых элементов — супер-категорию, представляющую объединение двух или более категорий.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Позволяет пакету VSPackage получать данные о шрифтах и цветах или сохранять их в реестре.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Уведомляет пакеты VSPackage, которые используют сведения о шрифтах и цвете для изменений в настройках шрифта и цвета.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Предоставляет средства для работы с входными и выходными данными, которые используются методами [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] механизма **шрифтов и цветов** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Контролирует кэширование параметров шрифта и цвета.  
  
## <a name="related-sections"></a>См. также  
 [Разработка языковой службы прежних версий](../extensibility/internals/developing-a-legacy-language-service.md)  
 Описывает, как пакеты VSPackage могут использовать языковые службы для настройки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] редактора.  
  
 [Цветовая маркировка синтаксиса в специализированных редакторах](../extensibility/syntax-coloring-in-custom-editors.md)  
 Дескриес, как [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Редактор использует языковые службы для реализации цветового выделения синтаксических конструкций.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Объясняется использование служб [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания элементов пользовательского интерфейса, соответствующих остальным частям [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].
