---
title: Страницы параметров и параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 963a73a3a8e079b2171c88e901913990892715cd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981899"
---
# <a name="options-and-options-pages"></a>Параметры и страницы параметров
При выборе пункта **Параметры** в меню **Сервис** открывается диалоговое окно **Параметры** . Параметры в этом диалоговом окне в совокупности называются страницами параметров. Элемент управления "дерево" в области навигации включает категории "Параметры", и каждая категория содержит страницы параметров. При выборе страницы ее параметры отображаются на правой панели. Эти страницы позволяют изменить значения параметров, определяющих состояние VSPackage.

## <a name="support-for-options-pages"></a>Поддержка страниц параметров
 Класс <xref:Microsoft.VisualStudio.Shell.Package> предоставляет поддержку для создания параметров страницы и категории параметров. Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует страницу параметров.

 Реализация <xref:Microsoft.VisualStudio.Shell.DialogPage> по умолчанию предлагает свои открытые свойства пользователю в универсальной сетке свойств. Это поведение можно настроить, переопределив различные методы на странице, чтобы создать страницу настраиваемых параметров, имеющую собственный пользовательский интерфейс. Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).

 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, который обеспечивает сохраняемость для страниц параметров, а также для параметров пользователя. Реализации методов <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> по умолчанию сохраняют изменения свойств в пользовательском разделе реестра, если это свойство можно преобразовать в строку и из нее.

## <a name="options-page-registry-path"></a>Путь к реестру страницы параметров
 По умолчанию путь реестра для свойств, управляемых страницей параметров, определяется сочетанием <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, слова DialogPage и имени типа для класса страницы Options. Например, класс страницы Options можно определить следующим образом.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, то пары имен и значений свойств являются подразделами HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Путь реестра страницы параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, Тулсоптионспажес, а также категории и имени страницы параметров. Например, если на странице «настраиваемые параметры» есть Категория «страница», «мои параметры» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> «HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp», то на странице «Параметры» содержится раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\ 8.0 exp \ Тулсоптионспажес \ мой параметр Пажес\кустом.

## <a name="toolsoptions-page-attributes-and-layout"></a>Атрибуты и макет страницы "Сервис/Параметры"
 Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> определяет группировку страниц настраиваемых параметров по категориям в дереве навигации диалогового окна **Параметры** . Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> связывает страницу параметров с пакетом VSPackage, предоставляющим интерфейс. Рассмотрим следующий фрагмент кода:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Это объявляет, что MyPackage предоставляет две страницы параметров: Оптионспажеженерал и Оптионспажекустом. В диалоговом окне **Параметры** обе страницы параметров отображаются в категории **Мои страницы** параметров как **Общие** и **Настраиваемые**соответственно.

## <a name="option-attributes-and-layout"></a>Атрибуты и макет параметров
 Пользовательский интерфейс, предоставляемый страницей, определяет внешний вид параметров на странице настраиваемых параметров. Макет, метки и описание параметров на странице универсальные параметры определяются следующими атрибутами.

- <xref:System.ComponentModel.CategoryAttribute> определяет категорию параметра.

- <xref:System.ComponentModel.DisplayNameAttribute> определяет отображаемое имя параметра.

- <xref:System.ComponentModel.DescriptionAttribute> определяет описание параметра.

  > [!NOTE]
  > Эквивалентные атрибуты, Сркатегори, Локдисплайнаме и Срдескриптион, используют строковые ресурсы для локализации и определяются в [примере управляемого проекта](/azure/devops/integrate/index).

  Рассмотрим следующий фрагмент кода:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Параметр Оптионинтежер отображается на странице Параметры в виде **целочисленного параметра** в категории **Мои параметры** . Если этот параметр выбран, в поле Описание отображается **параметр Description (мое целое число**).

## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страницам параметров из другого пакета VSPackage
 Пакет VSPackage, на котором размещается страница параметров и управляет им, может быть программно доступен из другого пакета VSPackage с помощью модели автоматизации. Например, в следующем коде пакет VSPackage регистрируется как размещенная страница параметров.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Следующий фрагмент кода получает значение Оптионинтежер из Мйоптионпаже:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Когда атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> регистрирует страницу параметров, эта страница регистрируется в ключе AutomationProperties, если `SupportsAutomation` аргумента атрибута имеет значение `true`. Автоматизация проверяет эту запись реестра, чтобы найти соответствующий пакет VSPackage, а затем автоматизирует доступ к свойству на странице "размещенные параметры", в данном случае на странице "Сетка".

 Путь реестра для свойства службы автоматизации определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, AutomationProperties, а также категории и имени страницы параметров. Например, если на странице «Параметры» имеется категория «моя Категория», имя страницы «Моя сетка» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, то свойство автоматизации имеет раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Страница сетки VisualStudio\8.0Exp\AutomationProperties\My Категори\ми.

> [!NOTE]
> Каноническое имя, страница Category.My Grid, является значением подраздела имени этого раздела.