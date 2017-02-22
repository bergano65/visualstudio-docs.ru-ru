---
title: "Параметры и параметры страницы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Параметры страницы [Visual Studio SDK] управляемых пакета framework поддержка средств"
  - "платформа управляемых пакетов, Сервис, параметры страницы поддержки"
  - "Сервис Параметры-страницы поддержки"
  - "Сервис Параметры-страницы [Visual Studio SDK] макеты"
  - "Сервис Параметры-страницы [Visual Studio SDK] атрибуты"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# Параметры и параметры страницы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Щелкнув **Параметры** на **средства** открывает меню **Параметры** диалоговое окно. Параметры в этом диалоговом окне Собирательно называются страницы параметров. Дерево в области переходов включает параметры категорий и каждая категория имеет параметры страницы. При выборе страницы ее содержимое отображается в правой области. Эти страницы позволяют изменять значения параметров, которые определяют состояние VSPackage.  
  
## Поддержка для страницы параметров  
 <xref:Microsoft.VisualStudio.Shell.Package> Обеспечивает поддержку для создания страниц параметры и параметры категории.<xref:Microsoft.VisualStudio.Shell.DialogPage> Класс реализует страницу параметров.  
  
 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает пользователю в виде универсального сетки свойств общих свойств. Это поведение можно настроить путем переопределения методов на странице, чтобы создать страницу настраиваемых параметров, которая имеет свой собственный пользовательский интерфейс \(UI\). Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, предоставляющее сохраняемости для страницы параметров, а также для настройки параметров пользователя. Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> методы сохранения изменений свойств в разделе реестра для пользователя, если свойство может быть преобразован в строку и обратно.  
  
## Путь в реестре параметры страницы  
 По умолчанию, пути в реестре свойств, управляемых страницу параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word DialogPage и имя типа класса страницы параметров. Например класс страницы параметров могут быть определены следующим образом.  
  
 [!CODE [VSSDKSupportForOptionsPages#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#1)]  
  
 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> является HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, то пар имени и значения свойств — это подразделы HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral.  
  
 Путь реестра самой страницы параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, ToolsOptionsPages и параметры страницы, категории и имени. Например, если пользовательская страница параметров имеет категорию Мои страницы параметр и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> — HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, то страницы параметров реестра, параметр Pages\\Custom HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My.  
  
## Атрибуты Сервис\/Параметры страницы и макета  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Атрибут определяет группирование пользовательских страниц параметров по категориям в дереве навигации **Параметры** диалоговое окно.<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Атрибут связывает страницу параметров с VSPackage, предоставляющий интерфейс. Рассмотрим следующий фрагмент кода:  
  
 [!CODE [VSSDKSupportForOptionsPages#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#2)]  
  
 Этот код объявляет, что MyPackage предоставляет две страницы параметров, OptionsPageGeneral и OptionsPageCustom. В **Параметры** диалоговом обоих параметров страницы отображаются **Мои страницы параметр** категории, **Общие** и **пользовательские**, соответственно.  
  
## Атрибуты параметра и макета  
 Пользовательского интерфейса \(UI\), страница определяет внешний вид параметры на странице настраиваемых параметров. Макет, метки и описание параметров на странице универсальные параметры определяются следующие атрибуты:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Определяет категорию параметра.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Определяет отображаемое имя параметра.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Определяет описание параметра.  
  
    > [!NOTE]
    >  Эквивалент атрибуты, SRCategory, LocDisplayName и SRDescription, использование строковых ресурсов для локализации и определены в [Пример управляемого проекта](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Рассмотрим следующий фрагмент кода:  
  
 [!CODE [VSSDKSupportForOptionsPages#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#3)]  
  
 Параметр OptionInteger появится на странице параметров как **вариант целое число** в **Параметры** категории. Если данный параметр выбран, описание, **Мой вариант целое**, отображается в поле «Описание».  
  
## Доступ к страницам параметры из другой VSPackage  
 VSPackage, который размещает и управляет страница «Параметры» можно получить доступ программными средствами из другой VSPackage при помощи модели автоматизации. Например в следующем коде VSPackage регистрируется как размещение страницы параметров.  
  
 [!CODE [VSSDKSupportForOptionsPages#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#4)]  
  
 Следующий фрагмент кода возвращает значение OptionInteger из MyOptionPage:  
  
 [!CODE [VSSDKSupportForOptionsPages#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#5)]  
  
 Когда <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> атрибут регистрирует страницу параметров, зарегистрированного в AutomationProperties ключа в том случае, если страница `SupportsAutomation` аргумент атрибута `true`. Автоматизация проверяет запись реестра для поиска связанных VSPackage и автоматизации, а затем обращается к свойству через размещенной странице параметры в этом случае мою страницу сетки.  
  
 Пути в реестре свойство определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, AutomationProperties и параметры страницы, категории и имени. Например, если параметры страницы категории Мои категории, имя Мои страницы сетки и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, то свойство имеет раздел реестра HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My Category\\My сеткой.  
  
> [!NOTE]
>  Каноническое имя мою страницу Category.My сетки, значение подраздела имя этого ключа.