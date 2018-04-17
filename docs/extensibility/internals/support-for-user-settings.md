---
title: Поддержка пользовательских параметров | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf2ba79cc8bff57de1fd410f8a2780825d693181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-user-settings"></a>Поддержка пользовательских параметров
VSPackage может определять один или несколько параметров категории, которые представляют собой группы переменных состояния, которые сохраняются, когда пользователь выбирает **Импорт и экспорт параметров** на **средства** меню. Чтобы включить этот сохраняемости, используйте API параметров в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Запись реестра, который называется точки настраиваемых параметров и GUID определяет категорию параметров VSPackage. VSPackage может поддерживать несколько категорий параметров, каждый из которых определяется точки настраиваемых параметров.  
  
-   Реализации параметров, которые основаны на сборки взаимодействия (с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> интерфейса) должны создавать точки настраиваемых параметров путем редактирования реестра или с помощью скрипта регистратора (RGS-файла). Дополнительные сведения см. в разделе [Создание скриптов регистратора](/cpp/atl/creating-registrar-scripts).  
  
-   Код, использующий Managed Package Framework (MPF) следует создать точек настраиваемых параметров путем присоединения <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> в пакет VSPackage для каждой точки настраиваемых параметров.  
  
     Если один пакет VSPackage поддерживает несколько точек настраиваемых параметров, каждой точки настраиваемых параметров реализуется отдельный класс, каждый из которых зарегистрирован с уникальный экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса. Следовательно параметры, класс реализации может поддерживать более одной категории параметров.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Подробные сведения о записи реестра точки настраиваемых параметров  
 Пользовательские параметры точки, созданные в запись реестра в следующем расположении: HKLM\Software\Microsoft\VisualStudio\\*\<версии >*\UserSettings\\`<CSPName>`, где `<CSPName>` — это имя точки настраиваемых параметров VSPackage поддерживает и  *\<версии >* версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 8.0.  
  
> [!NOTE]
>  Путь к корневому каталогу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<версии >* может быть переопределен с альтернативной корневой при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) инициализирован. Дополнительные сведения см. в разделе [параметры командной строки](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Ниже показана структура записи реестра.  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<версии >*\UserSettings\  
  
 `<CSPName`> = «#12345"s  
  
 Пакет = «{XXXXXX XXXX XXXX XXXX XXXXXXXXX}»  
  
 Категория = «{гггг ГГГГГГ гггг гггг YYYYYYYYY}»  
  
 ResourcePackage = «{ZZZZ ПППППП ZZZZ ZZZZ ZZZZZZZZZ}»  
  
 AlternateParent = «категория»  
  
|name|Тип|Данные|Описание|  
|----------|----------|----------|-----------------|  
|(Значение по умолчанию)|REG_SZ|Имя точки настраиваемых параметров|Имя ключа `<CSPName`>, нелокализованное имя точки настраиваемых параметров.<br /><br /> Для реализации основании MPF, его название получается путем объединения `categoryName` и `objectName` аргументы <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор в `categoryName_objectName`.<br /><br /> Ключ может быть пустым или может содержать идентификатор ссылки локализованные строки в DLL-Библиотеке дополнения. Это значение получается из `objectNameResourceID` аргумент <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор.|  
|Пакет|REG_SZ|Идентификатор GUID|Идентификатор GUID пакета VSPackage, реализующий точки настраиваемых параметров.<br /><br /> Зависимости от реализации с помощью MPF <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса, используйте конструктор `objectType` аргументу, содержащему VSPackage <xref:System.Type> и отражения для получения этого значения.|  
|Категория|REG_SZ|Идентификатор GUID|Идентификатор GUID, определяющий категорию параметров.<br /><br /> Для реализации на основе сборок взаимодействия, это значение может быть произвольно выбранных GUID, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] передает интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> методы. Все реализации этих двух методов необходимо проверить свои аргументы GUID.<br /><br /> Для реализации основании MPF, этот идентификатор GUID можно получить путем <xref:System.Type> класса, реализующего [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизм параметров.|  
|ResourcePackage|REG_SZ|Идентификатор GUID|Необязательный.<br /><br /> Путь к вспомогательные DLL которого содержит локализованные строки, если их нельзя указывать реализации VSPackage.<br /><br /> MPF использует отражение для получения необходимого ресурса VSPackage, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса не устанавливает этот аргумент.|  
|AlternateParent|REG_SZ|Имя папки в разделе Сервис — Параметры страницы, содержащей этот точки настраиваемых параметров.|Необязательный.<br /><br /> Это значение необходимо задать только в том случае, если параметры реализация поддерживает **Сервис — Параметры** страниц, использующих механизм сохраняемости в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] вместо механизм в модель автоматизации для сохранения состояния.<br /><br /> В данном случае является значение в ключе AlternateParent `topic` раздел `topic.sub-topic` строку, которая используется для идентификации конкретного **ToolsOptions** страницы. Например, для **ToolsOptions** страницы `"TextEditor.Basic"` значение AlternateParent бы `"TextEditor"`.<br /><br /> Когда <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> приводит к возникновению ошибки точки настраиваемых параметров, оно совпадает с именем категории.|