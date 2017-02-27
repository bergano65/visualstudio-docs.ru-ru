---
title: "Доступ к хранимой шрифта и цветов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "шрифты, доступ к сохраненным параметрам"
  - "шрифт и цвет элемента управления [Visual Studio SDK] сохраняемости"
  - "цвета, доступ к сохраненным параметрам"
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Доступ к хранимой шрифта и цветов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Интегрированной среды разработки (IDE) сохраняет измененные параметры шрифтов и цветов в реестре. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс для доступа к этим параметрам.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Для сохранения состояния сеансов шрифтов и цветов  
 Шрифт и цвет сведения по категориям в следующий раздел реестра: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\< версия Visual Studio>*\FontAndColors\\*\< CategoryGUID>*], где *\< CategoryGUID>* является GUID категории.  
  
 Таким образом Чтобы инициировать сохраняемости, VSPackage выполните следующие действия.  
  
-   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс путем вызова `QueryService` для глобального поставщика служб.  
  
     `QueryService` должен вызываться с помощью аргумента идентификатор службы `SID_SVsFontAndColorStorage` и аргумент идентификатора интерфейса `IID_IVsFontAndColorStorage`.  
  
-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод для открытия категория должна быть сохранена с помощью GUID категории и флаг режима как аргументы.  
  
     Режим, определяемое `fFlags` аргумент, создается на основе значений в <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> перечисления. Элементы управления в этом режиме.  
  
    -   Параметры, которые можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.  
  
    -   Все параметры или только те изменения пользователей и, которые доступны через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.  
  
    -   Способ распространения изменений в параметры пользователя.  
  
    -   Формат значения цвета, которые используются.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Для сохранения состояния использование шрифтов и цветов  
 Сохранение шрифтов и цветов включает в себя:  
  
-   Синхронизация параметров IDE с помощью параметров, хранящихся в реестре.  
  
-   Распространение сведения об изменении реестра.  
  
-   Установка и получение параметров, хранящихся в реестре.  
  
 Синхронизация параметр хранения с параметрами IDE почти незаметно. Базовой интегрированной среды Разработки автоматически запишет обновленные параметры для **Отображаемые элементы** к записям реестра категорий.  
  
 Если несколько пакетов VSPackages определенной категории, должна требовать VSPackage события, которые вызываются при методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса используются для изменения параметров хранимой реестра.  
  
 Создание событий не включен по умолчанию. Чтобы включить создание событий, категории необходимо открыть с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. В результате IDE для вызова соответствующего <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> метод, который реализует VSPackage.  
  
> [!NOTE]
>  Изменения через **шрифт и цвет** Страница свойств генерировать события независимо от <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление кэшированных параметров шрифта и цвета перед вызовом методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> класса.  
  
### <a name="storing-and-retrieving-information"></a>Хранения и извлечения сведений  
 Чтобы получить или настроить сведения, которые пользователь может изменить именованный отображения элемента в откройте категорию, вызовите VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> методы.  
  
 Сведения о шрифта атрибуты для определенной категории можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> методы.  
  
> [!NOTE]
>   `fFlags` Аргумент, передаваемый <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод при открытии этой категории определяет поведение <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы. По умолчанию эти методы возвращают только данные aboutdisplay itemsthat были изменены. Тем не менее если категория открыт с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> флаг, как обновить и может осуществляться без изменений отображаемые элементы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 По умолчанию изменен только **Отображаемые элементы** хранить данные в реестре.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс не может использоваться для извлечения всех параметров для шрифтов и цветов.  
  
> [!NOTE]
>   <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методы возвращают REGDB_E_KEYMISSING (0x80040152L) при их использовании для получения информации о неизменным **Отображаемые элементы**.  
  
 Параметры всех **Отображаемые элементы** в конкретной **категории** можно получить с помощью методов класса `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` интерфейса.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Реализация пользовательских категорий и отображения элементов](../extensibility/implementing-custom-categories-and-display-items.md)