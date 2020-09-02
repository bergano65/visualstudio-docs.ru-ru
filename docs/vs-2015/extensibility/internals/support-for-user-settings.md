---
title: Поддержка параметров пользователя | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80734d9859df2e06bc51d40e1fffa40c7d97c7a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691812"
---
# <a name="support-for-user-settings"></a>Поддержка параметров пользователя
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage может определять одну или несколько категорий параметров, которые являются группами переменных состояния, которые сохраняются, когда пользователь выбирает команду **Импорт/экспорт параметров** в меню **Сервис** . Чтобы включить эту сохраняемость, используйте API параметров в [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 Запись реестра, называемая пользовательской точкой параметров, а идентификатор GUID, определяет категорию параметров VSPackage. Пакет VSPackage может поддерживать несколько категорий параметров, каждый из которых определяется настраиваемой точкой параметров.  
  
- Реализации параметров, основанных на сборках взаимодействия (с использованием <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> интерфейса), должны создавать пользовательские точки параметров путем изменения реестра или использования скрипта регистратора (RGS-файла). Для получения дополнительной информации см. [Creating Registrar Scripts](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
- Код, использующий платформу Managed Package Framework (MPF), должен создавать точки настраиваемых параметров, присоединяя <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> к VSPackage для каждой точки настраиваемых параметров.  
  
     Если один пакет VSPackage поддерживает несколько точек настраиваемых параметров, каждая точка настраиваемых параметров реализуется отдельным классом, каждый из которых регистрируется уникальным экземпляром <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса. Следовательно, параметры, реализующие класс, могут поддерживать более одной категории параметров.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Сведения о записи реестра для точки пользовательских параметров  
 Пользовательские точки параметров создаются в записи реестра в следующем расположении: Хклм\софтваре\микрософт\висуалстудио \\ *\<Version>* \усерсеттингс \\ `<CSPName>` , где `<CSPName>` — это имя настраиваемых параметров, поддерживаемых VSPackage, а *\<Version>* — это версия [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , например 8,0.  
  
> [!NOTE]
> Корневой путь HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ *\<Version>* можно переопределить с помощью альтернативного корня при [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] инициализации интегрированной среды разработки (IDE). Дополнительные сведения см. в разделе [Параметры командной строки](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Структура записи реестра показана ниже:  
  
 Хклм\софтваре\микрософт\висуалстудио \\ *\<Version>* \усерсеттингс\  
  
 `<CSPName`>= s "#12345"  
  
 Package = "{XXXXXX XXXX XXXX XXXX XXXXXXXXX}"  
  
 Category = ' {ИИИИИИ гггг гггг гггг ИИИИИИИИИ} '  
  
 Ресаурцепаккаже = ' {ЗЗЗЗЗЗ ZZZZ ZZZZ ZZZZ ЗЗЗЗЗЗЗЗЗ} '  
  
 Алтернатепарент = Категория  
  
|Имя|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|(по умолчанию)|REG_SZ|Имя точки настраиваемых параметров|Имя ключа, `<CSPName`>, является нелокализованным именем точки настраиваемых параметров.<br /><br /> Для реализаций, основанных на MPF, имя ключа получается путем объединения `categoryName` аргументов и `objectName` <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктора в `categoryName_objectName` .<br /><br /> Ключ может быть пустым или содержать идентификатор ссылки на локализованную строку во вспомогательной библиотеке DLL. Это значение получается из `objectNameResourceID` аргумента в <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор.|  
|Пакет|REG_SZ|Код GUID|Идентификатор пакета VSPackage, который реализует пользовательскую точку параметров.<br /><br /> Реализации, основанные на MPF с помощью <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса, используют `objectType` для получения этого значения аргумент конструктора, содержащий VSPackage <xref:System.Type> и Reflection.|  
|Категория|REG_SZ|Код GUID|Идентификатор GUID, определяющий категорию параметров.<br /><br /> Для реализаций, основанных на сборках взаимодействия, это значение может быть произвольно выбираемым идентификатором GUID, который [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Среда IDE передает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> методам и. Все реализации этих двух методов должны проверять свои аргументы GUID.<br /><br /> Для реализаций, основанных на MPF, этот идентификатор GUID получается <xref:System.Type> классом, реализующим [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] механизм параметров.|  
|ResourcePackage|REG_SZ|Код GUID|Необязательный элемент.<br /><br /> Путь к вспомогательной библиотеке DLL, содержащей локализованные строки, если реализующий пакет VSPackage не предоставляет их.<br /><br /> MPF использует отражение для получения правильного пакета VSPackage ресурсов, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класс не задает этот аргумент.|  
|алтернатепарент|REG_SZ|Имя папки на странице параметров инструментов, содержащей эту точку настраиваемых параметров.|Необязательный элемент.<br /><br /> Это значение необходимо задавать только в том случае, если реализация параметров поддерживает страницы **параметров инструментов** , которые используют механизм сохраняемости в, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] а не механизм в модели автоматизации для сохранения состояния.<br /><br /> В этих случаях значение в ключе Алтернатепарент является `topic` разделом `topic.sub-topic` строки, используемой для задания конкретной **тулсоптионс** страницы. Например, для страницы **тулсоптионс** `"TextEditor.Basic"` значение алтернатепарент будет `"TextEditor"` .<br /><br /> При <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> создании точки настраиваемых параметров она совпадает с именем категории.|
