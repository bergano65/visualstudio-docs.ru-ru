---
title: "Использование страниц параметров | Microsoft Docs"
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
  - "страницы параметров средств [Visual Studio SDK], использование"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# Использование страниц параметров
Модель автоматизации [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предоставляет объект <xref:EnvDTE.DTE>, чтобы позволить пакетам VSPackage доступ к диалоговому окну **Параметры** в меню **Сервис**.  
  
 Как правило, к страницам в диалоговом окне **Параметры** можно получить доступ с помощью модели автоматизации, независимо от того, предоставляются ли эти страницы интегрированной средой разработки \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или пакетом VSPackage. Однако существуют следующие исключения.  
  
-   Программный доступ к параметрам страницы **динамической справки** невозможен. Компонентом **Динамическая справка** можно управлять с помощью модели автоматизации, но управление должно выполняться непосредственно в коде. Дополнительные сведения см. в разделе [How to: Control the Dynamic Help Window](http://msdn.microsoft.com/ru-ru/7f5777aa-c270-4058-a175-8ce8a4ed25eb).  
  
-   Управление параметрами страницы **Шрифты и цвета** осуществляется через ее собственный API, а не с помощью модели автоматизации. Для получения дополнительной информации см. [Шрифты и цвета](../extensibility/using-fonts-and-colors.md).  
  
-   Свойства, зависящие от языка, нельзя получить с помощью модели автоматизации.  
  
 Страницы **параметров**, которые не поддерживают модель автоматизации [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], могут не возвращать коллекцию <xref:EnvDTE.Properties> автоматизации при запросе. Если коллекция возвращается, присутствуют не все функции. Сведения об управлении этими функциями см. в разделе [Коллекции свойств DTE](../Topic/DTE%20Properties%20Collections.md).  
  
## Управление страницами параметров  
 Для управления страницами **параметров** VSPackage должен получить объект <xref:EnvDTE.DTE> из модели автоматизации.  
  
> [!NOTE]
>  Когда VSPackage использует модель автоматизации для запроса и изменения параметров на установленных страницах **параметров**, он не расширяет функциональность IDE. Таким образом, этот пакет не должен реализовывать объект автоматизации.  
  
 Для получения объекта <xref:EnvDTE.DTE> с помощью модели автоматизации вызовите метод <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> и предоставьте аргумент идентификатора службы `SID_SDTE` и аргумент интерфейса `IID__DTE`, как показано ниже.  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 Для получения объекта <xref:EnvDTE.DTE> с помощью Managed Package Framework \(MPF\) вызовите метод <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> и предоставьте параметр `serviceType` типа <xref:Microsoft.VisualStudio.Shell.Interop.SDTE>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 Страница **параметров** задается с помощью двух идентификаторов. Первый идентификатор — это строка, указывающая папку, которая содержит страницу **параметров**. Второй идентификатор — это строка, указывающая конкретный элемент в этой папке. Они называются категорией и подкатегорией страницы **параметров** или ее разделом и подразделом.  
  
 Например, параметры текстового редактора для обработки кода Basic присутствуют в области навигации как член **Basic** папки **Text Editor**. Идентификатор этой категории — `TextEditor`, ее подкатегории — `Basic`, а сама страница **параметров** называется `TextEditor.Basic`.  
  
> [!NOTE]
>  В целях локализации и по другим причинам имена, отображаемые на странице **параметров**, могут отличаться от строк, используемых в качестве идентификаторов категории и подкатегории. Может потребоваться использование автоматизации для запроса IDE, чтобы получить правильные идентификаторы, если они нигде не задокументированы. В реестре они располагаются в разделе HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<версия VS\>*\\AutomationProperties, где *\<версия VS\>* — это номер версии выпуска [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Для получения дополнительной информации см. [Регистрация пользовательских страниц параметров](../misc/registering-custom-options-pages.md).  
  
 Вы можете получить свойства для страницы `TextEditor.Basic` через модель автоматизации, используя приведенный ниже пример.  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 Для получения свойств с помощью MPF используйте метод <xref:EnvDTE._DTE.Properties%2A>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 Метод <xref:EnvDTE.Properties.Item%2A> возвращает отдельные параметры из коллекции <xref:EnvDTE.Properties> как объект <xref:EnvDTE.Property>.  
  
 Аналогично категориям и подкатегориям, каждый параметр имеет идентификатор, который является уникальной строкой. Например, параметр **Размер шага табуляции** на странице `TextEditor.Basic` идентифицируется строкой `TabSize`.  
  
> [!NOTE]
>  В целях локализации и по другим причинам имена, отображаемые на странице **параметров**, могут отличаться от строк, используемых в качестве идентификаторов параметров. Может потребоваться использование автоматизации для запроса IDE, чтобы получить правильные идентификаторы, если они нигде не задокументированы.  
  
 Для запроса и изменения состояния параметров можно использовать значение <xref:EnvDTE.Property.Value%2A> объекта <xref:EnvDTE.Property>, возвращаемого методом <xref:EnvDTE.Properties.Item%2A> коллекции <xref:EnvDTE.Properties>.  
  
 Например, чтобы задать параметр **Размер шага табуляции** на странице `TextEditor.Basic` с помощью модели автоматизации, используйте объект <xref:EnvDTE.Properties>, возвращаемый в следующем примере.  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 В следующем примере демонстрируется обновление параметра **Размер шага табуляции** с помощью MPF.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 Для получения дополнительной информации см. [Управление параметрами](../Topic/Controlling%20Options%20Settings.md).  
  
## Сохранение параметров страницы параметров  
 IDE реализует сохранение состояния страниц **параметров** страниц с полной поддержкой модели автоматизации [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Параметры на страницах, которые включены в IDE, автоматически сохраняются \(или извлекаются\), когда пользователь щелкает команду **Импорт и экспорт параметров** в меню **Сервис**.  
  
 Вы можете включить использование этой поддержки автоматического сохранения для вашей пользовательской страницы **параметров**, добавив флаг `ProfileSave` в запись реестра этой страницы **параметров** в разделе HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<версия VS\>*\\AutomationProperties, где *\<версия VS\>* является номером версии выпуска [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [Регистрация пользовательских страниц параметров](../misc/registering-custom-options-pages.md).  
  
## См. также  
 [Создание страниц "Параметры" с помощью сборок взаимодействия](/visual-cpp/misc/creating-options-pages-by-using-interop-assemblies)   
 [Создание страницы параметров](../extensibility/internals/creating-options-pages.md)   
 [Создание страниц "Параметры" с помощью автоматизации](../misc/creating-options-pages-by-using-automation.md)   
 [Управление параметрами](../Topic/Controlling%20Options%20Settings.md)   
 [Регистрация пользовательских страниц параметров](../misc/registering-custom-options-pages.md)   
 [Открытие страницы параметров](../misc/opening-an-options-page.md)   
 [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)