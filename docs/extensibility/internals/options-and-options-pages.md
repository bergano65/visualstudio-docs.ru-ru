---
title: Параметры и параметры страницы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d85b900779a5df8af077b292b2e2f70b0592e35c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="options-and-options-pages"></a>Параметры и параметры страницы
Щелкнув **параметры** на **средства** открывает меню **параметры** диалоговое окно. Параметры в этом диалоговом Собирательно называются страницы параметров. Дерево в области переходов включает параметры категорий, а каждая категория имеет параметры страницы. При выборе страницы ее содержимое отображается в правой области. Эти страницы позволяют изменить значения параметров, которые определяют состояния пакета VSPackage.  
  
## <a name="support-for-options-pages"></a>Поддержка для страницы параметров  
 <xref:Microsoft.VisualStudio.Shell.Package> Класс обеспечивает поддержку для создания страницы параметров и параметров категорий. <xref:Microsoft.VisualStudio.Shell.DialogPage> Класс реализует страницу параметров.  
  
 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает пользователю в виде универсального сетки свойств его открытые свойства. Это поведение можно настроить путем переопределения методов на странице, чтобы создать настраиваемые параметры страницу, которая имеет свой собственный пользовательский интерфейс (UI). Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> Класс реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, который обеспечивает механизм сохраняемости для страницы параметров, а также для пользовательских параметров. Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> методы сохранения изменений свойств в раздел реестра пользователя, если свойство может быть преобразовано в строку и обратно.  
  
## <a name="options-page-registry-path"></a>Путь в реестре параметры страницы  
 По умолчанию, путь реестра для свойств, управляемых объектом страницу параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word DialogPage и имя типа класса страницы параметров. Например класс страницы параметров могут быть определены следующим образом.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> является HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, а затем пар имен и значений свойств — это подразделы HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ Company.OptionsPage.OptionsPageGeneral.  
  
 Путь в реестре параметры страницы определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, категории и имя страницы слова, ToolsOptionsPages и параметры. Например, если настраиваемой страницы параметров содержит категории, Мои страницы параметров и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> является HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, страница «Параметры» содержит раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Pages\Custom VisualStudio\8.0Exp\ToolsOptionsPages\My параметр.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Атрибуты Сервис/Параметры страницы и макета  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Атрибут определяет группирования пользовательских страниц параметров по категориям в дереве навигации **параметры** диалоговое окно. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Атрибут связывает страницу параметров с пакетом VSPackage, предоставляющий интерфейс. Рассмотрим следующий фрагмент кода:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 Объявляет, что MyPackage предоставляет две страницы параметров, OptionsPageGeneral и OptionsPageCustom. В **параметры** диалоговое окно, как параметры страницы отображаются **Мои страницы параметров** категории как **Общие** и **настраиваемый**соответственно.  
  
## <a name="option-attributes-and-layout"></a>Атрибуты параметра и макет  
 Пользовательский интерфейс (UI), страница предоставляет определяет внешний вид параметры на странице пользовательские параметры. Макет, пометки и описание параметров на странице универсальные параметры определяются следующие атрибуты:  
  
-   <xref:System.ComponentModel.CategoryAttribute> Определяет категорию параметра.  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> Определяет отображаемое имя параметра.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> Определяет описание параметра.  
  
    > [!NOTE]
    >  Эквивалент атрибуты, SRCategory, LocDisplayName и SRDescription, использование строковых ресурсов для локализации и определены в [образец управляемого проекта](http://go.microsoft.com/fwlink/?LinkId=122774).  
  
 Рассмотрим следующий фрагмент кода:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 Этот параметр OptionInteger отображается на странице "Параметры", на **целочисленный параметр** в **параметры моей** категории. Если параметр выбран, описание, **Мой целочисленный параметр**, отображается в поле «Описание».  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страницы параметров из другого пакета VSPackage  
 Пакет VSPackage, который размещает и управляет страницу параметров можно получить доступ программными средствами из другого пакета VSPackage с помощью модели автоматизации. Например в следующем коде VSPackage регистрируется как размещение страницу параметра.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 В следующем фрагменте кода возвращает значение OptionInteger из MyOptionPage:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 Когда <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> атрибут регистрирует страница «Параметры», страница регистрируется области при ключа AutomationProperties `SupportsAutomation` аргумент атрибута `true`. Автоматизация проверяет этой записи реестра для поиска связанных VSPackage и автоматизации, а затем обращается к свойству через размещенную страницу параметров, в этом случае Мой страница «Сетка».  
  
 Пути в реестре свойство определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, категории и имя страницы слова, AutomationProperties и параметры. Например, если параметры страницы категории Мои категории, имя My страница «Сетка» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, то свойство имеет раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\VisualStudio\8.0Exp\AutomationProperties\My страница Category\My «сетка».  
  
> [!NOTE]
>  Каноническое имя My Category.My страница «Сетка», значение подраздела имя этого ключа.