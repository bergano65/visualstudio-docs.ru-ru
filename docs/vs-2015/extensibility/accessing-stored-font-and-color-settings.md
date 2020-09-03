---
title: Доступ к сохраненным параметрам шрифта и цвета | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821832"
---
# <a name="accessing-stored-font-and-color-settings"></a>Доступ к хранимым параметрам шрифтов и цветов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Интегрированная среда разработки (IDE) сохраняет измененные параметры для шрифтов и цветов в реестре. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Для доступа к этим параметрам можно использовать интерфейс.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Инициация сохранения состояния шрифтов и цветов  
 Сведения о шрифтах и цветах хранятся по категориям в следующем разделе реестра: [Хкку\софтваре\микрософт \Висуал Studio \\ *\<Visual Studio version>* \фонтандколорс \\ *\<CategoryGUID>* ], где *\<CategoryGUID>* — это GUID категории.  
  
 Таким образом, для инициации сохраняемости VSPackage должен:  
  
- Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс, вызвав по `QueryService` отношению к поставщику глобальных служб.  
  
     `QueryService` должен вызываться с помощью аргумента идентификатора службы `SID_SVsFontAndColorStorage` и аргумента идентификатора интерфейса `IID_IVsFontAndColorStorage` .  
  
- Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод, чтобы открыть категорию для сохранения с помощью GUID категории и флага режима в качестве аргументов.  
  
  Режим, заданный `fFlags` аргументом, формируется из значений в <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> перечислении. Этот режим управляет:  

  - Параметры, к которым можно получить доступ через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.  

  - Либо все параметры, либо только те, которые пользователи изменяют и извлекают через <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейс.  

  - Способ распространения изменений параметров пользователя.  

  - Формат значений цвета, которые используются.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Использование сохраняемости состояния шрифтов и цветов  
 Сохранение шрифтов и цветов включает в себя:  
  
- Синхронизация параметров интегрированной среды разработки с параметрами, хранящимися в реестре.  
  
- Распространение сведений об изменении реестра.  
  
- Установка и извлечение параметров, хранимых в реестре.  
  
  Синхронизация настроек хранилища с параметрами IDE в значительной степени прозрачна. Базовая интегрированная среда разработки автоматически записывает обновленные параметры для **отображаемых элементов** в записи реестра категорий.  
  
  Если несколько пакетов VSPackage совместно используют определенную категорию, то пакет VSPackage должен потребовать, чтобы события создавались, когда методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса используются для изменения сохраненных параметров реестра.  
  
  По умолчанию создание событий не включено. Чтобы включить создание событий, необходимо открыть категорию с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . В результате интегрированная среда разработки вызывает соответствующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> метод, который реализует VSPackage.  
  
> [!NOTE]
> Изменения на странице свойств **Шрифт и цвет** создают события независимо от <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Можно использовать интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> чтобы определить, требуется ли обновление кэшированных параметров шрифта и цвета перед вызовом методов <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> класса.  
  
### <a name="storing-and-retrieving-information"></a>Хранение и извлечение информации  
 Чтобы получить или настроить сведения, которые пользователь может изменить для именованного отображаемого элемента в открытой категории, пакеты VSPackage вызывают <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> методы и.  
  
 Сведения о атрибутах шрифтов для определенной категории получаются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методов и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> .  
  
> [!NOTE]
> `fFlags`Аргумент, который передается в <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> метод при открытии этой категории, определяет поведение <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> методов и. По умолчанию эти методы возвращают только сведения абаутдисплай итемссат. Однако если категория открыта с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> флага, то к обновленным и неизмененным отображаемым элементам могут обращаться <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 По умолчанию в реестре сохраняются только сведения об измененных **отображаемых элементах** . <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Интерфейс нельзя использовать для получения всех параметров для шрифтов и цветов.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Методы и возвращают REGDB_E_KEYMISSING (0x80040152L) при их использовании для получения сведений о неизмененных **отображаемых элементах**.  
  
 Параметры всех **отображаемых элементов** в определенной **категории** можно получить с помощью методов `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` интерфейса.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Реализация пользовательских категорий и отображаемых элементов](../extensibility/implementing-custom-categories-and-display-items.md)
