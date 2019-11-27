---
title: Страницы параметров и параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e30be26c40834d3122d491f8d150f02b6f3b776
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300691"
---
# <a name="options-and-options-pages"></a>Параметры и страницы параметров
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При выборе пункта **Параметры** в меню **Сервис** открывается диалоговое окно **Параметры** . Параметры в этом диалоговом окне в совокупности называются страницами параметров. Элемент управления "дерево" в области навигации включает категории "Параметры", и каждая категория содержит страницы параметров. При выборе страницы ее параметры отображаются на правой панели. Эти страницы позволяют изменить значения параметров, определяющих состояние VSPackage.  
  
## <a name="support-for-options-pages"></a>Поддержка страниц параметров  
 Класс <xref:Microsoft.VisualStudio.Shell.Package> предоставляет поддержку для создания параметров страницы и категории параметров. Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует страницу параметров.  
  
 Реализация <xref:Microsoft.VisualStudio.Shell.DialogPage> по умолчанию предлагает свои открытые свойства пользователю в универсальной сетке свойств. Это поведение можно настроить, переопределив различные методы на странице, чтобы создать страницу настраиваемых параметров, имеющую собственный пользовательский интерфейс. Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).  
  
 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, который обеспечивает сохраняемость для страниц параметров, а также для параметров пользователя. Реализации методов <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> по умолчанию сохраняют изменения свойств в пользовательском разделе реестра, если это свойство можно преобразовать в строку и из нее.  
  
## <a name="options-page-registry-path"></a>Путь к реестру страницы параметров  
 По умолчанию путь реестра для свойств, управляемых страницей параметров, определяется сочетанием <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, слова DialogPage и имени типа для класса страницы Options. Например, класс страницы Options можно определить следующим образом.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp, то пары имен и значений свойств являются подразделами HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.  
  
 Путь реестра страницы параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, Тулсоптионспажес, а также категории и имени страницы параметров. Например, если на странице «настраиваемые параметры» есть страница «Категория», «мои параметры» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, то на странице «Параметры» будет указан раздел реестра HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Пажес\кустом.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Атрибуты и макет страницы "Сервис/Параметры"  
 Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> определяет группировку страниц настраиваемых параметров по категориям в дереве навигации диалогового окна **Параметры** . Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> связывает страницу параметров с пакетом VSPackage, предоставляющим интерфейс. Рассмотрим следующий фрагмент кода:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Это объявляет, что MyPackage предоставляет две страницы параметров: Оптионспажеженерал и Оптионспажекустом. В диалоговом окне **Параметры** обе страницы параметров отображаются в категории **Мои страницы** параметров как **Общие** и **Настраиваемые**соответственно.  
  
## <a name="option-attributes-and-layout"></a>Атрибуты и макет параметров  
 Пользовательский интерфейс, предоставляемый страницей, определяет внешний вид параметров на странице настраиваемых параметров. Макет, метки и описание параметров на странице универсальные параметры определяются следующими атрибутами.  
  
- <xref:System.ComponentModel.CategoryAttribute> определяет категорию параметра.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> определяет отображаемое имя параметра.  
  
- <xref:System.ComponentModel.DescriptionAttribute> определяет описание параметра.  
  
  > [!NOTE]
  > Эквивалентные атрибуты, Сркатегори, Локдисплайнаме и Срдескриптион, используют строковые ресурсы для локализации и определяются в [примере управляемого проекта](https://go.microsoft.com/fwlink/?LinkId=122774).  
  
  Рассмотрим следующий фрагмент кода:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Параметр Оптионинтежер отображается на странице Параметры в виде **целочисленного параметра** в категории **Мои параметры** . Если этот параметр выбран, в поле Описание отображается **параметр Description (мое целое число**).  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страницам параметров из другого пакета VSPackage  
 Пакет VSPackage, на котором размещается страница параметров и управляет им, может быть программно доступен из другого пакета VSPackage с помощью модели автоматизации. Например, в следующем коде пакет VSPackage регистрируется как размещенная страница параметров.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Следующий фрагмент кода получает значение Оптионинтежер из Мйоптионпаже:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Когда атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> регистрирует страницу параметров, эта страница регистрируется в ключе AutomationProperties, если `SupportsAutomation` аргумента атрибута имеет значение `true`. Автоматизация проверяет эту запись реестра, чтобы найти соответствующий пакет VSPackage, а затем автоматизирует доступ к свойству на странице "размещенные параметры", в данном случае на странице "Сетка".  
  
 Путь реестра для свойства службы автоматизации определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, AutomationProperties, а также категории и имени страницы параметров. Например, если на странице «Параметры» имеется категория «моя Категория», имя страницы «Моя сетка» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp, то свойство автоматизации содержит раздел реестра HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Категори\ми Page (сетка).  
  
> [!NOTE]
> Каноническое имя, страница Category.My Grid, является значением подраздела имени этого раздела.
