---
title: Новые возможности пакета SDK для Visual Studio 2015 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917333"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Новые&#39;возможности пакета SDK для Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет SDK для Visual Studio содержит следующие новые и обновленные функции Visual Studio 2015, обновления Visual Studio 2015 и Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

Начиная с Visual Studio 2017, поиск пользовательских шаблонов проектов и элементов больше не будет выполняться. Вместо этого расширение должно предоставлять файлы манифеста шаблона, описывающие расположение установки этих шаблонов. Для обновления расширений VSIX можно использовать Visual Studio 2017. При развертывании расширения с помощью MSI необходимо создать файлы манифеста шаблона вручную. Дополнительные сведения см. в разделе [Обновление пользовательских шаблоны проектов и элементов для Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Схема манифеста шаблона описана в [справочнике по схеме манифеста шаблона Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Пакет SDK для VS 2015 с обновлением 1
 Обновление 1 включает в себя средства, помогающие вашему расширению работать с цветовыми темами и службой образов Visual Studio.

 Эти разделы находятся в разделе [Служебные программы VSSDK](../extensibility/internals/vssdk-utilities.md) :

- Эти [инструменты](../extensibility/internals/color-theming-tools.md) позволяют создавать и редактировать пользовательские цвета для Visual Studio.

- [Средства службы образов](../extensibility/internals/image-service-tools.md) позволяют работать с файлами манифеста изображений Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Новый способ добавления пакета SDK для Visual Studio в Visual Studio
 Начиная с Visual Studio 2015 вам не нужно загружать пакет SDK для Visual Studio отдельно. Вместо этого вы можете установить его в рамках обычного процесса установки или установить его позже. При открытии или создании решения VSIX Visual Studio предложит установить средства расширения Visual Studio. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Новые способы создания расширений
 Начиная с пакета SDK для Visual Studio 2015, у вас есть различные варианты создания расширений в зависимости от используемого языка программирования.

### <a name="visual-c-and-visual-basic"></a>Visual C# и Visual Basic
 Для C# и Visual Basic существует полный спектр шаблонов элементов проекта, позволяющих создавать пакеты VSPackage, команды меню, окна инструментов, классификаторы редактора, элементы редактора и расширения полей редактора. Можно добавить любые или все из них в стандартный проект VSIX. Дополнительные сведения см. в следующих разделах.

- [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Мастер VSPackage больше не создает расширения в C# или Visual Basic.

### <a name="c"></a>C++
 Для C++, мастер VSPackage поддерживает команды меню, окна инструментов и пользовательские редакторы. Найдите его в диалоговом окне **Новый проект** в **Visual C++ /Extensibility**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Эталонные сборки пакета SDK VS через NuGet
 Для повышения переносимости и совместного использования проектов расширяемости можно использовать версии NuGet справочных сборок пакета VS SDK.  Они доступны в [NuGet.org](https://www.nuget.org/) , опубликованном [висуалстудиоекстенсибилити](https://www.nuget.org/profiles/VisualStudioExtensibility) , и могут быть легко добавлены в проект или решение с помощью Visual Studio **References/Manage NuGet Packages** . Можно добавить отдельные ссылки на конкретные сборки расширения или добавить все сборки для VS SDK одновременно с помощью [мета пакета](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)пакета SDK vs. Дополнительные сведения о NuGet см. в статье [Общие сведения о NuGet](/nuget/) и [Управление пакетами NuGet с помощью диалогового окна](/nuget/consume-packages/install-use-packages-visual-studio).

 При использовании версий NuGet эталонных сборок пакета Visual Studio другой пользователь не должен устанавливать пакет SDK VS для открытия и сборки проекта.  Для этого проекта на компьютере будут автоматически установлены эталонные сборки NuGet и средства сборки SDK VS.

 Шаблоны элементов пакета VS SDK используют NuGet для своих ссылок и средств сборки, поэтому вы получаете преимущества NuGet по умолчанию.

> [!NOTE]
> Вы можете продолжать использовать установленные эталонные сборки пакета VS SDK в своих проектах (расположенном в каталоге \<установки Visual Studio > \ Вссдк\висуалстудиоинтегратион\коммон\ассемблиес), а существующие проекты расширяемости не нуждаются в обновлении для использования пакетов NuGet.  Диалоговое окно **ссылки на проект/добавить ссылку** продолжит использовать установленные эталонные сборки пакета VS SDK.
>
> Если вы хотите изменить существующие проекты для использования NuGet, см. раздел [как перенести пакеты VSPackage в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) с разделом по обновлению проектов расширяемости в пакетах NuGet.

## <a name="light-bulbs"></a>Лампочки
 Один из наиболее интересных способов написания кода расширения предоставляется проектом Roslyn. Дополнительные сведения см. в разделе [Roslyn](https://github.com/dotnet/Roslyn).

 Лампочки — это новая функция, которая поставляется вместе с VSSDK. Они представляют собой значки, используемые в редакторе Visual Studio, которые разворачиваются для отображения набора действий рефакторинга кода или исправлений для проблем, определяемых встроенными анализаторами кода. Дополнительные сведения см. в разделе [Пошаговое руководство. Отображение предложений](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)с лампочкой.

## <a name="updated-user-experience-guidelines"></a>Обновленные рекомендации по работе с пользователем
 Разрабатывая новые расширения или функции для Visual Studio? Ознакомьтесь с обновленными и расширенными [рекомендациями по работе с пользователем Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Вы найдете [маркеры цветов](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [размеры шрифтов](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [спецификации диалоговых окон](../extensibility/ux-guidelines/layout-for-visual-studio.md)и другие рекомендации, необходимые для беспрепятственной интеграции нового пользовательского интерфейса с Visual Studio.
