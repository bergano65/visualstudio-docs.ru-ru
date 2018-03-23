---
title: Доступ к хранимой шрифта и цветов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 78fc7c343cc570742d2d246a60d3093485800132
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="accessing-stored-font-and-color-settings"></a>Доступ к хранимой шрифта и цветов
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) сохраняет измененные параметры для шрифтов и цветов в реестре. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс для доступа к этим параметрам.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Чтобы инициировать сохранения состояния шрифтов и цветов
 Шрифт и цвет сведения по категориям в следующий раздел реестра: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >*\FontAndColors\\  *\<CategoryGUID >*], где  *\<CategoryGUID >* является GUID категории.

 Таким образом Чтобы инициировать постоянного хранения, пакет VSPackage должен:

-   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса путем вызова `QueryService` к поставщику глобальной службы.

     `QueryService` должен вызываться с помощью аргумент идентификатора службы `SID_SVsFontAndColorStorage` и аргумент идентификатора интерфейса `IID_IVsFontAndColorStorage`.

-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод, чтобы открыть категорию следует сохранять при помощи GUID категории и флаг режима в качестве аргументов.

     Режим, заданные `fFlags` аргумент, создается на основе значений в <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> перечисления. Элементы управления в этом режиме.

    -   Параметры, которые можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.

    -   Все параметры или только те параметры, изменять пользователей и который извлекаются через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.

    -   Способ распространения изменений в параметры пользователя.

    -   Формат значения цвета, которые используются.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Для сохранения состояния использование шрифтов и цветов
 Включает сохранение шрифты и цвета.

-   Синхронизация параметров IDE с параметрами, хранимыми в реестре.

-   Распространение сведения об изменении реестра.

-   Установка и получение параметров, хранящихся в реестре.

 Во многом прозрачно синхронизации параметру хранения с параметрами интегрированной среды разработки. Базовой интегрированная среда разработки автоматически запишет обновленные параметры для **отображаемые элементы** к записям реестра категорий.

 Если несколько пакетов VSPackage для определенной категории, VSPackage должна требовать события, которые вызываются при методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса используются для изменения параметров реестра хранимой.

 Генерирование событий не включен по умолчанию. Чтобы включить создание событий, категории должно быть установлено с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Открытие категорию вызывает интегрированной среды разработки для вызова соответствующего <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> метода, реализующего пакет VSPackage.

> [!NOTE]
>  Изменения через **шрифт и цвет** страницу свойств создавать события независимо от <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление кэшированных параметров шрифта и цвета перед вызовом методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> класса.

### <a name="storing-and-retrieving-information"></a>Хранение и получение сведений о
 Чтобы получить или настроить сведения, которые пользователь может изменить для отображения именованного элемента в категорию откройте, вызовите пакеты VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> методы.

 Сведения о шрифта атрибуты для определенной категории получается с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> методы.

> [!NOTE]
>  `fFlags` Аргумента, переданного в <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод во время открытия этой категории определяет поведение <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы. По умолчанию эти методы возвращают только сведения о отображаемые элементы, которые были изменены. Тем не менее если категория открыт с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> флаг, как обновить и может осуществляться без изменений отображаемые элементы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 По умолчанию изменено только **отображаемые элементы** хранить данные в реестре. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Интерфейс не может использоваться для извлечения всех параметров для шрифтов и цветов.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> И <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы возвращают REGDB_E_KEYMISSING (0x80040152L), когда вы используете их для получения сведений о неизменным **отображаемые элементы**.

 Параметры всех **отображаемые элементы** в определенном **категории** можно получить с помощью методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейса.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Реализация пользовательских категорий и отображаемые элементы](../extensibility/implementing-custom-categories-and-display-items.md)