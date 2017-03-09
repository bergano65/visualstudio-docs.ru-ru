---
title: "Регистрация пользовательских страниц параметров | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "регистрация, пользовательские страницы в окне "Сервис Параметры""
  - "страницы "Сервис Параметры" [пакет SDK для Visual Studio], регистрация"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# Регистрация пользовательских страниц параметров
Для страницы **Сервис параметры**, которые должны быть доступны для пользователей и автоматизация поддержки, он должен быть правильно зарегистрировать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с интегрированной средой разработки \(ide\).  
  
 Страницы **Сервис параметры** на основе управляемых области пакета, зарегистрированных путем применения экземпляр <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> в VSPackage, предоставляющий страницу.  Поддержка автоматизации отображается путем задания свойства <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> к `true`.  
  
## Регистрация страницы " сервис Параметры "  
 Интегрировать настраиваемую страницу **Сервис параметры** с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] требует создания записей реестра в следующем расположении: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>*\\ToolsOptionsPages, где *\<Версия\>* — это версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 8.0.  
  
 Запись имеет первичный ключ с категорией \(`<PageCategory>`\) страницы **Сервис параметры** и подраздел содержит имя подкатегории страницы \(`<PageSubCategory>`\).  
  
 Например, страница **Сервис параметры** указанной строкой, **TextEditor.Basic**, имеет \=textEditor `<PageCategory>` раздела реестра с подразделом `<PageSubCategory>`\=Basic.  
  
 Структура записи реестра ниже:  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Версия\>*\\ToolsOptionsPages\\  
  
 `<PageCategory>` \= '\#12345'  
  
 Package \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 ResourcePackage \= '{YYYYYY YYYY YYYY YYYY YYYYYYYYY}'  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Версия\>*\\ToolsOptionsPages\\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 Page \= '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 Package \= '{AAAAAA AAAA AAAA AAAA AAAAAAAAA}'  
  
 ResourcePackage \= '{BBBBBB BBBB BBBB BBBB BBBBBBBBB}'  
  
 NoShowAllView \= 0\/1  
  
 В следующей таблице перечислены значения в разделе реестра HKLM\\Software\\Microsoft\\VisualStudio\\*\<Версия\>*\\ToolsOptionsPages\\`<PageCategory>`.  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|\(Значение по умолчанию\)|REG\_SZ|Каноническое имя категории пользовательской страницы **Сервис параметры**|Имя клавиши, `<PageCategory>`, каноническое нелокализованное имя категории страницы **Сервис параметры**. **Note:**  Если автоматизация поддерживается, то канонические non\-локализованные имена категорий и подкатегорий используются, чтобы получить коллекцию <xref:EnvDTE.Properties> страницы **Сервис параметры**.  Дополнительные сведения см. в разделе [Использование страниц параметров](../misc/using-options-pages.md). <br /><br /> Для реализаций на основе управляемых области пакета, \> `<PageCategory` получено из аргументов `categoryName` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.<br /><br /> Стрелка может быть пустой или она может содержать идентификатор ссылки на локализованную строку в реализации вспомогательной библиотеки DLL.<br /><br /> Для реализаций на основе управляемых области пакета, это значение получено из аргументов `categoryResourceID` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.|  
|Пакет|REG\_SZ|GUID|Идентификатор GUID VSPackage, реализующий пользовательскую страницу **Сервис параметры**.<br /><br /> Реализации на основе управляемых области пакета с помощью отражения использования <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для получения этого значения.|  
|ResourcePackage|REG\_SZ|GUID|Необязательный.<br /><br /> Вспомогательной библиотеки DLL, содержащей локализованные строки, если при реализации VSPackage не передает их.<br /><br /> Управляемые границы пакета используют отражение для получения правильного пакет ресурсов, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> не устанавливает этот аргумент.|  
  
 В следующей таблице перечислены значения в разделе реестра HKLM\\Software\\Microsoft\\VisualStudio\\*\<Версия\>*\\ToolsOptionsPages\\`<PageCategory>`\\`<PageSubCategory>`.  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|\(Значение по умолчанию\)|REG\_SZ|Каноническое имя подкатегории пользовательской страницы **Сервис параметры**|Имя клавиш, \> `<PageSubCategory`, каноническое нелокализованное имя подкатегории страницы **Сервис параметры**. **Note:**  Если автоматизация поддерживается, то канонические non\-локализованные имена категорий и подкатегорий используются, чтобы получить коллекцию <xref:EnvDTE.Properties> страницы **Сервис параметры**.  Дополнительные сведения см. в разделе [Использование страниц параметров](../misc/using-options-pages.md). <br /><br /> Для реализаций на основе управляемых области пакета, \> `<PageSubegory` получено из аргументов `pageName` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.<br /><br /> Стрелка может быть пустой или она может содержать идентификатор ссылки на локализованную строку в вспомогательной библиотеки DLL реализации.<br /><br /> Для реализаций на основе управляемых области пакета, это значение получено из аргументов `pageNameResourceID` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.|  
|Страница|REG\_SZ|GUID|Идентификатор GUID объекта, реализующий пользовательскую страницу **Сервис параметры**.<br /><br /> Реализации на основе управляемых области пакета с помощью <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> использующие аргумент `pageType` конструктора, содержащий <xref:System.Type> и отражение VSPackage для получения этого значения.|  
|Пакет|REG\_SZ|GUID|Реализации на основе управляемых области пакета с помощью отражения использования <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для получения этого значения.|  
|ResourcePackage|REG\_SZ|GUID|Необязательный.<br /><br /> Вспомогательной библиотеки DLL, содержащей локализованные строки, если при реализации VSPackage не передает их.<br /><br /> Управляемые границы пакета используют отражение для получения правильную библиотеку ресурсов, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> не устанавливает этот аргумент.|  
|NoShowAllView|REG\_DWORD|0 или 1|Необязательный.<br /><br /> Указывает, должна ли заданный страница **Сервис параметры** отображаться в сложное \(по умолчанию\) представление страниц **Сервис параметры**.  Поддерживает программные среды, например Visual Basic, которые имеют специальные страницы **Сервис параметры** для статистической обработки общих параметров для предоставления пользователям со специализированными упрощенными представлениями параметров.<br /><br /> Если запись REG\_DWORD безнулева, страница **Сервис параметры** не отображается в сложное представление.<br /><br /> Дополнительные сведения см. в разделе [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md).<br /><br /> Реализации на основе управляемых области пакета, могут установить это значение путем задания свойства <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A> к `true` в конструкторе <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.|  
  
 VSPackage или объект на основе одной сборке взаимодействия могут реализовывать более одной страницы **Сервис параметры**.  Каждая реализация требует новой записи в HKLM\\Software\\Microsoft\\VisualStudio\\*\<Версия\>*\\ToolsOptionsPages.  
  
 По мере того, как управляемые создает структуры пакета объект, предоставляющий страницу **Сервис параметры** каждая страница должны иметь свой собственный объект реализации, независимо от реализации VSPackage <xref:Microsoft.VisualStudio.Shell.Package>.  
  
## Поддержка автоматизации  
 Если поддержка автоматизации используется для реализации страницу **Сервис параметры**, она должна зарегистрировать как поставщик автоматизации.  Для использования автоматизации для управления свойствами и использования его механизмов сохраняемости сохранение состояния веб\-страницы **Сервис параметры**, он должен зарегистрировать как поставщик `AutomationProperty`.  
  
### Зарегистрируйте VSPackage как поставщик автоматизации \(только для страниц Параметры средств на основе сборках взаимодействия\)  
 Страницы **Сервис параметры** на основе сборке взаимодействия реализуются как часть классов реализации VSPackage.  
  
 В этом случае, если страница **Сервис параметры** поддержки автоматизации VSPackage сборка\-основанное взаимодействия должен быть зарегистрирован как поставщик автоматизации.  
  
> [!NOTE]
>  Поддержка автоматизации в управляемых области пакета обеспечивается независимым объекта реализации VSPackage.  Если этот объект поддерживает автоматизацию, то это свойство <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> зарегистрирован с помощью конструктора <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.  
  
 Запись регистрации VSPackage как поставщик автоматизации формы HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>*\\Packages\\*\<PackageGUID\>*\\Automation, где *\<Версия\>* — это версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(например 8.0\) и *\<PackageGUID\>* — это GUID VSPackage реализующий объект автоматизации.  
  
> [!NOTE]
>  Путь корневого раздела HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>* можно переопределить с корнем при инициализации оболочки Visual Studio.  Дополнительные сведения см. в разделе [Параметры командной строки](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Структура записи реестра:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>*\\Packages\\*\<PackageGUID\>*\\Automation  
  
 `<AutomationObjectName>`  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|Автоматизация|REG\_SZ|Не указано|Не определено.<br /><br /> Присутствие данного ключа указывает, что VSPackage, на который указывает *\<PackageGUID\>*, поддерживает автоматизацию.<br /><br /> Поля можно использовать для хранения документация.<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> автоматически создает эта клавиша для управляемых приложений, основанных на платформе пакета.|  
|`<AutomationObjectName>`|REG\_SZ|Каноническое имя указанного объекта автоматизации|Является значимым только имя ключа.  Он используется в операциях автоматизации.<br /><br /> Поля можно использовать для хранения документация.<br /><br /> Для реализаций на основе управляемых области пакета, имя данной клавиши указано аргументом `name` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>.<br /><br /> Если конструктор имеет допустимое строковое <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> передаваемое его свойству <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A>, то это значение будет вставлено здесь.|  
  
### Зарегистрируйте эту страницу параметров средств, таких как поддержка автоматических тестов  
 Управляемые среды и реализации пакетов и взаимодействия сборка\-основанного страниц **Сервис параметры** необходимо зарегистрировать, чтобы разрешить доступ к странице **Сервис параметры** автоматизации.  Это обеспечивает механизмы и к сохраняемости свойства автоматизации к странице через <xref:EnvDTE>.  Это независимый сам регистрации VSPackage как поставщик услуг автоматизации.  
  
 Например, при регистрации страницы **Сервис параметры** упомянутая выше запись имеет первичный ключ с категорией \(`<PageCategory>`\) страницы **Сервис параметры** и подраздел содержит имя подкатегории страницы \(`<PageSubcategory>`\).  
  
 При использовании управляемых границы пакета, используйте <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для регистрации класса, как предоставление страницу **Сервис параметры** и задать свойство <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>`true`, чтобы указать, что страница поддерживает автоматизацию.  
  
 Запись реестра находится в HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>*\\AutomationProperties, где *\<Версия\>* — это версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 8.0.  
  
> [!NOTE]
>  Путь корня HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>* можно переопределить с корнем оболочки Visual Studio при инициализации для получения дополнительных сведений см. [Параметры командной строки](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 Структура записи реестра ниже:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>\\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= «{}»  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 Пакет \= «{YYYYYY ГГГГ ГГГГ ГГГГ YYYYYYYYY}»  
  
 Имя \= «`<PageCategory>` .`<PageSubcategory>`»  
  
 «ProfileSave» \= 1\/0  
  
 В следующей таблице перечислены значения в разделе HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>*\\AutomationProperties\\`<PageCategory>`.  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|\(Значение по умолчанию\)|REG\_SZ|Каноническое имя категории пользовательской страницы **Сервис параметры**|Имя клавиш, \> `<PageCategory`, каноническое нелокализованное имя категории страницы **Сервис параметры**. **Note:**  Если автоматизация поддерживается, то канонические non\-локализованные имена категорий и подкатегорий используются, чтобы получить коллекцию <xref:EnvDTE.Properties> страницы **Сервис параметры**.  Дополнительные сведения см. в разделе [Использование страниц параметров](../misc/using-options-pages.md). <br /><br /> Стрелка может быть пустой или она может содержать идентификатор ссылки на локализованную строку в реализации вспомогательной библиотеки DLL.<br /><br /> Для реализаций на основе управляемых области пакета, \> `<PageCategory` получено из аргументов `categoryName` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.|  
|ResourcePackage|REG\_SZ|GUID|Необязательный.<br /><br /> Вспомогательной библиотеки DLL, содержащей локализованные строки, если при реализации VSPackage не передает их.<br /><br /> Управляемые границы пакета используют отражение для получения правильного ресурс VSPackage, поэтому <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> не устанавливает этот аргумент.|  
  
 В следующей таблице перечислены значения в разделе HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Версия\>*\\AutomationProperties\\`<PageCategory>\<PageSubCategory>`.  
  
|Имя|Тип|Данные|Описание|  
|---------|---------|------------|--------------|  
|\(Значение по умолчанию\)|REG\_SZ|Имя подкатегории пользовательской страницы **Сервис параметры**|Имя клавиш, \> `<PageSubCategory`, каноническое нелокализованное имя подкатегории страницы **Сервис параметры**. **Note:**  Если автоматизация поддерживается, то канонические non\-локализованные имена категорий и подкатегорий используются, чтобы получить коллекцию <xref:EnvDTE.Properties> страницы **Сервис параметры**.  Дополнительные сведения см. в разделе [Использование страниц параметров](../misc/using-options-pages.md). <br /><br /> Стрелка может быть пустой или она может содержать идентификатор ссылки на локализованную строку в реализации вспомогательной библиотеки DLL.<br /><br /> Для реализаций на основе управляемых области пакета, `<PageSubCategory>` получено из аргументов `pageName` в конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>.|  
|Пакет|REG\_SZ|GUID|Идентификатор GUID VSPackage, реализующий пользовательскую страницу **Сервис параметры**.<br /><br /> Реализации на основе управляемых области пакета с помощью отражения использования <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для получения этого значения.|  
|Имя|REG\_SZ|Имя коллекции свойств страницы **Сервис параметры**|Строка `<PageCategory>.<PageSubCategory>`, используемая для обращения к странице **Сервис параметры**.  Дополнительные сведения см. в разделе [Использование страниц параметров](../misc/using-options-pages.md).<br /><br /> Для реализаций на основе управляемых области пакета, имя получено из аргументов конструктора <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> и формы `categoryName.pageName`.|  
|ProfileSave|DWORD|1\/0|Необязательный.<br /><br /> Это значение указывает, сохраняются ли настройки страницы параметров **Сервис параметры** механизмом [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], когда пользователь выбирает соответствующую команду **Параметры импорта\-экспорта** в меню **Сервис**.<br /><br /> Если клавиша присутствует, а его значение равно 1, то страница **Сервис параметры** запрашивает поддержку параметров.<br /><br /> Реализации на основе управляемых области пакета устанавливают это значение, если предоставляют конструктор <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> со свойством <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> к `true`.|  
  
## См. также  
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Использование страниц параметров](../misc/using-options-pages.md)   
 [Создание страниц "Параметры" с помощью сборок взаимодействия](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Практическое руководство. Создание пользовательских страниц параметров](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Страницы параметров](../misc/options-pages.md)   
 [Поддержка модели автоматизации для страницы параметров](../extensibility/internals/automation-support-for-options-pages.md)