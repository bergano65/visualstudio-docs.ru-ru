---
title: "Шрифты и цвета | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "шрифты, управление в интегрированной среде разработки"
  - "Интегрированная среда разработки, управление шрифты и цвета текста"
  - "Страница свойств шрифтов и цветов"
  - "шрифт и цвет элемента управления [Visual Studio SDK]"
  - "текст, интегрированной среды разработки"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Шрифты и цвета
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] предоставляет поддержку использования шрифтов и цветов отображаемый текст.  
  
## В этом подразделе  
 [Обзор цвета и шрифта](../extensibility/font-and-color-overview.md)  
 Описывает параметры шрифта и цвета текста [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки \(ide\).  Также вводит основные понятия категорий и папок отображения и описывает способы и использование редактора VSPackages вставке СМС основные атрибуты.  
  
 [Получение шрифта и цвет шрифта для текста цветом](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Содержит рекомендации по реализации колоризацию текста в VSPackages, которые управляют **Категории** except  **Текстовый редактор**.  
  
 [Доступ к хранимой шрифта и цветов](../extensibility/accessing-stored-font-and-color-settings.md)  
 Объясняет, как текущие параметры шрифта и цвета могут храниться, получение и применения.  
  
 [Реализация пользовательских категорий и отображения элементов](../extensibility/implementing-custom-categories-and-display-items.md)  
 Описывает основные шаги, окно может создать и использует его из **Отображаемые элементы** и  **Категории** поддержка отображение текста.  
  
 Этот подход требует VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс и связанные интерфейсы.  
  
 [Практическое руководство: доступ к встроенных шрифтов и цветовой схемы](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Содержит сведения о том, как определить и зарегистрировать категорию с помощью встроенных шрифтов и цветов и инициирует использование системные шрифты и цвета.  
  
## Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Предоставляет экземпляр `IVsFontAndColorDefaults` или  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> интерфейс, соответствующий указанному элементу, перечисленных в виде  **Параметры для** в списке  **Шрифты и цвета** страница   **Параметры** диалоговое окно.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Разрешает VSPackage, чтобы поддерживать интегрированную среду разработки **Шрифты и цвета** страница с указанием шрифты и цвета по умолчанию для окна или компонента пользовательского интерфейса.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Обеспечивает механизм, с помощью которого VSPackage, предоставляющий поддержка шрифта и цвета может определить группы папок отображения \- супер\-категорию, представляющий собой объединение двух или более категорий.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Разрешает VSPackage, чтобы получить данные шрифта и цвета и сохраняет его в реестр.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Уведомляет VSPackages, которое использует данные шрифта и цвета об изменениях в параметрах шрифта и цвета.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Предоставляет средства для работы с входными данными и выходных продукциями, используемые методами [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Шрифт и цвет** механизм.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Контролирует кэширование параметры шрифта и цвета.  
  
## Связанные подразделы  
 [Разработка службы языка](../extensibility/internals/developing-a-legacy-language-service.md)  
 Обсуждается VSPackages может использовать для настройки службы языка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор.  
  
 [В редакторах синтаксиса](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries как [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] редактор использует службы языка для реализации расцветку синтаксиса.  
  
 [Расширение других частей Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Описание использования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] службы для создания элементов пользовательского интерфейса которых совпадают с остальноям  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].