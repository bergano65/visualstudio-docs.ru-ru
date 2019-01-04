---
title: Доступ к хранимой шрифтов и цветов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a3c4738923c4b187ea6a55e5f6b52f550f7442d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990913"
---
# <a name="access-stored-font-and-color-settings"></a>Доступ хранимой параметры шрифта и цвета
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) сохраняет измененные параметры шрифтов и цветов в реестре. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс для доступа к этим параметрам.

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Чтобы начать сохранение состояния шрифты и цвета
 Данные шрифта и цвета хранится по категориям в следующий раздел реестра: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], где  *\<CategoryGUID >* является GUID категории.

 Таким образом Чтобы инициировать сохраняемости, пакет VSPackage должен:

-   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс путем вызова `QueryService` от глобальный поставщик служб.

     `QueryService` должен вызываться с помощью аргумент идентификатора службы `SID_SVsFontAndColorStorage` и аргумент идентификатор интерфейса `IID_IVsFontAndColorStorage`.

-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод для открытия категории, которые необходимо сохранить, используя GUID категории в и флаг режима в качестве аргументов.

     Режим, определяемое `fFlags` аргумент, создается на основе значений в <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> перечисления. Элементы управления в этом режиме.

    -   Параметры, которые можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.

    -   Все параметры или только те параметры, изменить пользователей и который можно получить через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.

    -   Способ добавления изменений в параметры пользователя.

    -   Формат значений цвета, которые используются.

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Чтобы использовать сохранение состояния шрифты и цвета
 Сохранение шрифты и цвета состоит из:

- Синхронизация параметров интегрированной среды разработки с помощью параметров, хранящихся в реестре.

- Распространение сведения об изменении реестра.

- Установка и получение параметров, хранящихся в реестре.

  Синхронизации с параметрами интегрированной среды разработки параметр хранилища почти незаметно. Базовой интегрированной среды разработки автоматически записывает обновленные параметры для **отображаемые элементы** для записи в реестре категорий.

  Потребуется ли несколько пакетов VSPackage, общий доступ к определенной категории, VSPackage приводятся события при методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса используются для изменения параметров хранимой реестра.

  Создание событий не включена по умолчанию. Чтобы включить создание событий, категории необходимо открыть с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Открытие категорию инициирует IDE для вызова соответствующего <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> метод, реализующий VSPackage.

> [!NOTE]
>  Изменения через **шрифта и цвета** страницу свойств создают события, независимо от <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление кэшированных параметры шрифта и цвета, перед вызовом методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> класса.

### <a name="store-and-retrieve-information"></a>Store и получение сведений о
 Чтобы получить или настроить сведения, которые пользователь может изменить для отображения именованного элемента в категории, открытой, вызовите пакетов VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> методы.

 Сведения о шрифта атрибуты для определенной категории, получены с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> методы.

> [!NOTE]
>  `fFlags` Аргумент, передаваемый <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод во время открытия этой категории определяет поведение <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы. По умолчанию эти методы возвращают только сведения об отображаемых элементов, которые были изменены. Тем не менее если категория открыт с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> флаг, оба обновления и может осуществляться без изменений отображаемые элементы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.

 По умолчанию изменены только **отображаемые элементы** информация хранится в реестре. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Интерфейс не может использоваться для извлечения всех параметров для шрифтов и цветов.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> И <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы возвращают REGDB_E_KEYMISSING (0x80040152L) при их использовании для получения сведений о неизменным **отображаемые элементы**.

 Параметры всех **отображаемые элементы** в определенном **категории** можно получить с помощью методов класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> интерфейс.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [Реализовать пользовательские категории и отображать элементы](../extensibility/implementing-custom-categories-and-display-items.md)