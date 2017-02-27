---
title: "Поддержка параметров пользователя | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Пользовательские параметры точек"
  - "Регистрация поддержка сохраняемости параметров пользователя [Visual Studio SDK]"
  - "Сохранение состояния, регистрации параметры"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Поддержка параметров пользователя
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage может определять одну или несколько категорий параметры, которые переменных состояния, которые сохраняются, когда пользователь нажимает **импорта и экспорта параметров** на **средства** меню. Чтобы это сохраняемости, следует использовать API параметров в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Запись реестра, называется пользовательской настройки точки и GUID определяет категорию параметров VSPackage. VSPackage может поддерживать несколько категорий параметров, все определенные точкой пользовательские параметры.  
  
-   Реализации параметров, которые основаны на сборки взаимодействия \(с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> интерфейса\) следует создавать пользовательские параметры точки путем редактирования реестра или с помощью скрипта регистратора \(RGS\-файла\). Для получения дополнительной информации см. [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
-   Код, который использует управляемые пакета Framework \(MPF\) следует создать пользовательские параметры точек путем присоединения <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> пакет VSPackage для каждой точки пользовательские параметры.  
  
     Если один VSPackage поддерживает несколько точек пользовательские параметры, параметры каждой пользовательской точки реализуется отдельный класс и каждый регистрируется с помощью уникального экземпляра <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса. Следовательно параметры, реализация класса может поддерживать более чем одной категории параметров.  
  
## Подробные сведения о записи реестра точки пользовательские параметры  
 Пользовательские параметры точки, созданные в запись реестра в следующем расположении: HKLM\\Software\\Microsoft\\VisualStudio\\*\< версия \>*\\UserSettings\\`<CSPName>`, где `<CSPName>` — имя пользовательской настройки точки поддерживает VSPackage и *\< версия \>* версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], например 8.0.  
  
> [!NOTE]
>  Путь к корневому каталогу HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< версия \>* может быть переопределен с альтернативной корневых при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инициализируется интегрированной среды разработки \(IDE\). Для получения дополнительной информации см. [Параметры командной строки](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Ниже показана структура записи реестра.  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< версия \>*\\UserSettings\\  
  
 `<CSPName`\> \= «\#12345"s  
  
 Пакет \= «{XXXXXX XXXX XXXX XXXX XXXXXXXXX}»  
  
 Категория \= «{гггг YYYYYY гггг гггг YYYYYYYYY}»  
  
 ResourcePackage \= «{ZZZZ ПППППП ZZZZ ZZZZ ZZZZZZZZZ}»  
  
 AlternateParent \= «категория»  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|\(Значение по умолчанию\)|REG\_SZ|Имя пользовательской настройки точки|Имя ключа, `<CSPName`\>, нелокализованное имя пользовательской настройки точки.<br /><br /> Для реализации в зависимости от MPF, имя ключа получается путем объединения `categoryName` и `objectName` аргументы <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Конструктор в `categoryName_objectName`.<br /><br /> Ключ может быть пустым или содержать идентификатор ссылки локализованную строку в вспомогательную библиотеку DLL. Это значение получается из `objectNameResourceID` аргумент <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> конструктор.|  
|Пакет|REG\_SZ|GUID|Идентификатор GUID VSPackage, который реализует пользовательской настройки точки.<br /><br /> Реализации основаны на использовании MPF <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса, используйте конструктор `objectType` аргументу, содержащему VSPackage <xref:System.Type> и отражение для получения этого значения.|  
|Категория|REG\_SZ|GUID|Идентификатор GUID, определяющий категорию параметров.<br /><br /> Для реализации в зависимости от сборок взаимодействия, это значение может быть произвольно выбранным GUID, который [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] передает IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> методы. Все реализации этих двух методов необходимо проверить свои аргументы GUID.<br /><br /> Этот идентификатор GUID для реализации в зависимости от MPF, полученный посредством <xref:System.Type> класса, реализующего [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] механизм настройки.|  
|ResourcePackage|REG\_SZ|GUID|Необязательный.<br /><br /> Путь к вспомогательные DLL которого содержит локализованные строки, если их нельзя указывать реализации VSPackage.<br /><br /> MPF использует отражение для получения необходимого ресурса VSPackage, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> класса не устанавливает этот аргумент.|  
|AlternateParent|REG\_SZ|Имя папки в Сервис Параметры страницы, содержащей эту точку пользовательские параметры.|Необязательный.<br /><br /> Необходимо задать это значение только в том случае, если параметры реализация поддерживает **Сервис Параметры** страниц, использующих механизм сохранения в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] вместо механизма в модели автоматизации для сохранения состояния.<br /><br /> В этих случаях — значение в ключе AlternateParent `topic` раздел `topic.sub-topic` строку, используемую для идентификации конкретного **средстваПараметры** страницы. Например, **средстваПараметры** страница `"TextEditor.Basic"` значение AlternateParent будет иметь `"TextEditor"`.<br /><br /> Когда <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> создает точку пользовательские параметры же, что имя категории.|