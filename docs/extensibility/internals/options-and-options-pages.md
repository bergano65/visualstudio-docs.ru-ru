---
title: Страницы вариантов и опций Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706841"
---
# <a name="options-and-options-pages"></a>Параметры и страницы параметров
Нажатие **параметры** в меню **Инструменты** открывает поле диалога **Параметры.** Параметры в этом диалоговом поле коллективно называются страницами вариантов. Управление деревом в навигационном стеле включает в себя категории опций, и каждая категория имеет страницы вариантов. При выборе страницы ее параметры отображаются в правом стене. Эти страницы позволяют изменить значения параметров, определяющих состояние VSPackage.

## <a name="support-for-options-pages"></a>Поддержка страниц опционов
 Класс <xref:Microsoft.VisualStudio.Shell.Package> обеспечивает поддержку для создания страниц вариантов и категорий вариантов. Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует страницу опций.

 Реализация по <xref:Microsoft.VisualStudio.Shell.DialogPage> умолчанию предлагает свои общедоступные свойства пользователю в общей сетке свойств. Вы можете настроить это поведение, переопределив различные методы на странице, чтобы создать пользовательскую страницу опций, которая имеет свой собственный пользовательский интерфейс (UI). Для получения дополнительной информации [см.](../../extensibility/creating-an-options-page.md)

 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> <xref:Microsoft.VisualStudio.Shell.IProfileManager>реализует, который обеспечивает сохранение для страниц вариантов, а также для настроек пользователя. Реализации и <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> методы по умолчанию сохраняют изменения свойств в разделе пользователя реестра, если свойство может быть преобразовано в строку и из нее.

## <a name="options-page-registry-path"></a>Путь регистрации страниц вариантов
 По умолчанию путь реестра свойств, управляемых страницей <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>опционов, определяется путем объединения, слова DialogPage и имени типа класса страницы опционов. Например, класс страницы параметров может быть определен следующим образом.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> это HKEY_CURRENT_USER-Программное обеспечение,Microsoft-VisualStudio,8.0Exp, то имя свойства и пары значений являются подключаемыми HKEY_CURRENT_USER»Software»Microsoft-VisualStudio-8.0Exp-DialogPage-Компания.OptionsPage.OptionsPageGeneral.

 Путь реестра самой страницы опционов <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>определяется путем объединения, слова, ToolsOptionsPages, а также категории страницы опций и имени. Например, если страница пользовательских опций имеет категорию, My Option Pages, и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio,8.0Exp, то страница вариантов имеет ключ реестра, HKEY_LOCAL_MACHINE»-ПРОГРАММЫ-Microsoft-VisualStudio-8.0Exp-ToolsOptionsPages-My Option Pages-Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Атрибуты страницы инструментов/опционов и планировка
 Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> определяет группировку пользовательских страниц опций в категории в навигационном дереве диалогового окна **Options.** Атрибут <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> связывает страницу опций с VSPackage, который предоставляет интерфейс. Рассмотрим следующий фрагмент кода:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Это объявляет, что MyPackage предоставляет два варианта страницы, OptionsPageGeneral и OptionsPageCustom. В диалоговом поле **Options** обе страницы опций отображаются в категории **My Option Pages** как **общие** и **пользовательские**соответственно.

## <a name="option-attributes-and-layout"></a>Атрибуты опций и планировка
 Пользовательский интерфейс (UI), который предоставляетстраница, определяет внешний вид параметров на странице пользовательских опций. Макет, маркировка и описание параметров на странице общих опций определяются следующими атрибутами:

- <xref:System.ComponentModel.CategoryAttribute>определяет категорию опциона.

- <xref:System.ComponentModel.DisplayNameAttribute>определяет имя отображения опции.

- <xref:System.ComponentModel.DescriptionAttribute>определяет описание опции.

  > [!NOTE]
  > Эквивалентные атрибуты, SRCategory, LocDisplayName и SRDescription используют строковые ресурсы для локализации и определяются в [управляемом примере проекта.](/azure/devops/integrate/index)

  Рассмотрим следующий фрагмент кода:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Опция OptionInteger отображается на странице опций в качестве **варианта Integer** в категории **My Options.** Если вариант выбран, описание, **Мой вариант integer**, появляется в поле описания.

## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страницам опционов из другого VSPackage
 VSPackage, который размещает и управляет страницей опций, может быть программно доступен из другого VSPackage с помощью модели автоматизации. Например, в следующем коде VSPackage зарегистрирован как хостинг страницы опции.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Следующий фрагмент кода получает значение OptionInteger от MyOptionPage:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 Когда <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> атрибут регистрирует страницу опций, страница регистрируется под `SupportsAutomation` ключом AutomationProperties, если аргумент атрибута . `true` Автоматизация проверяет эту запись реестра, чтобы найти связанный VSPackage, и автоматизация затем получает доступ к свойству через страницу размещенных опций, в данном случае, My Grid Page.

 Путь реестра свойства автоматизации определяется <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>путем объединения, слова, AutomationProperties, а также категории страницы опций и имени. Например, если страница опций имеет категорию Моя Категория, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>имя страницы My Grid, а также , HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp, то свойство автоматизации имеет ключ реестра, HKEY_LOCAL_MACHINE»SOFTWARE-Microsoft-VisualStudio-8.0Exp-AutomationProperties-My Category-My Grid Page.

> [!NOTE]
> Каноническое название, My Category.My Grid Page, является значением подключаемого ключа "Имя".
