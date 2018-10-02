---
title: Доступ к хранимой шрифтов и цветов | Документация Майкрософт
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
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3387c5e611ad12ce81347e51893e8459ecd9a3c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560028"
---
# <a name="accessing-stored-font-and-color-settings"></a>Доступ к хранимой шрифтов и цветов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [параметры доступа к хранятся шрифта и цвета](https://docs.microsoft.com/visualstudio/extensibility/accessing-stored-font-and-color-settings).  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Интегрированной среды разработки (IDE) сохраняет измененные параметры шрифтов и цветов в реестре. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс для доступа к этим параметрам.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Чтобы начать сохранение состояния шрифтов и цветов  
 Данные шрифта и цвета хранится по категориям в следующий раздел реестра: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<версия Visual Studio >* \FontAndColors\\  *\<CategoryGUID >*], где  *\<CategoryGUID >* является GUID категории.  
  
 Таким образом Чтобы инициировать сохраняемости, пакет VSPackage должен:  
  
-   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс путем вызова `QueryService` от глобальный поставщик служб.  
  
     `QueryService` должен вызываться с помощью аргумент идентификатора службы `SID_SVsFontAndColorStorage` и аргумент идентификатор интерфейса `IID_IVsFontAndColorStorage`.  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод для открытия категории, которые необходимо сохранить, используя GUID категории в и флаг режима в качестве аргументов.  
  
     Режим, определяемое `fFlags` аргумент, создается на основе значений в <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> перечисления. Элементы управления в этом режиме.  
  
    -   Параметры, которые можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.  
  
    -   Все параметры или только те пользователи изменять и который можно получить через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.  
  
    -   Способ добавления изменений в параметры пользователя.  
  
    -   Формат значений цвета, которые используются.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Для сохранения состояния использования шрифтов и цветов  
 Сохранение шрифты и цвета состоит из:  
  
-   Синхронизация параметров интегрированной среды разработки с помощью параметров, хранящихся в реестре.  
  
-   Распространение сведения об изменении реестра.  
  
-   Установка и получение параметров, хранящихся в реестре.  
  
 Синхронизации с параметрами интегрированной среды разработки параметр хранилища почти незаметно. Базовой интегрированной среды разработки автоматически записывает обновленные параметры для **отображаемые элементы** для записи в реестре категорий.  
  
 Потребуется ли несколько пакетов VSPackage, общий доступ к определенной категории, VSPackage приводятся события при методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса используются для изменения параметров хранимой реестра.  
  
 Создание событий не включена по умолчанию. Чтобы включить создание событий, категории необходимо открыть с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Это приводит к интегрированной среде разработки для вызова соответствующего <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> метод, реализующий VSPackage.  
  
> [!NOTE]
>  Изменения через **шрифта и цвета** страницу свойств создают события, независимо от <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление кэшированных параметры шрифта и цвета, перед вызовом методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> класса.  
  
### <a name="storing-and-retrieving-information"></a>Хранения и извлечения сведений  
 Чтобы получить или настроить сведения, которые пользователь может изменить для отображения именованного элемента в категории, открытой, вызовите пакетов VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> методы.  
  
 Сведения о шрифта атрибуты для определенной категории, получены с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> методы.  
  
> [!NOTE]
>  `fFlags` Аргумент, передаваемый <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод во время открытия этой категории определяет поведение <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы. По умолчанию эти методы только возвращают сведения aboutdisplay itemsthat были изменены. Тем не менее если категория открыт с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> флаг, оба обновления и может осуществляться без изменений отображаемые элементы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 По умолчанию изменены только **отображаемые элементы** информация хранится в реестре. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Интерфейс не может использоваться для извлечения всех параметров для шрифтов и цветов.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> И <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы возвращают REGDB_E_KEYMISSING (0x80040152L) при их использовании для получения сведений о неизменным **отображаемые элементы**.  
  
 Параметры всех **отображаемые элементы** в определенном **категории** можно получить с помощью методов класса `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` интерфейс.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Реализация пользовательских категорий и отображаемых элементов](../extensibility/implementing-custom-categories-and-display-items.md)

