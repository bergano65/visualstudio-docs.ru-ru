---
title: Что&#39;возможности пакета SDK для Visual Studio 2015 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a67b2e1d9cbbad4a9b3426d264e6fecf8623e5a7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105094"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Что&#39;возможности пакета SDK для Visual Studio 2015
Пакет SDK для Visual Studio имеет следующие новые и обновленные функции для Visual Studio 2015, обновление Visual Studio 2015 и Visual Studio 2017.

## <a name="vs-2015-sdk-update-1"></a>Обновления пакета SDK для Visual STUDIO 2015 1
 Обновление 1 включает в себя средства для работы с функцией цветовые темы и службы образов в Visual Studio расширение.

 Эти разделы находятся под [служебные программы VSSDK](../extensibility/internals/vssdk-utilities.md) раздел:

- [Цвета темы средства](../extensibility/internals/color-theming-tools.md) позволяют создавать и изменять собственные цвета для Visual Studio.

- [Изображения средства service](../extensibility/internals/image-service-tools.md) позволяют работать с файлами манифеста изображений Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Новый способ добавить пакет SDK для Visual Studio в Visual Studio
 Начиная с Visual Studio 2015, не нужно отдельно скачать пакет SDK для Visual Studio. Вместо этого его можно установить как часть процесса Обычная установка, или вы можете установить его позже. При открытии или создании решение VSIX, Visual Studio предложит установить средства расширения Visual Studio. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Новые способы создания расширений
 Начиная с пакета SDK для Visual Studio 2015, у вас есть различные параметры для создания расширений, в зависимости от того, какой язык программирования, на который вы используете.

### <a name="visual-c-and-visual-basic"></a>Visual C# и Visual Basic
 Для C# и Visual Basic имеется полный набор шаблонов элементов проекта, которые позволяют создавать пакеты VSPackage, команды меню, окна инструментов, редактор классификаторы, элементов оформления редактора и margin расширения редактора. Стандартный проект VSIX можно добавить любые или все из этих шаблонов. Дополнительные сведения:

- [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     Мастер VSPackage больше не создает расширения в C# или Visual Basic.

### <a name="c"></a>C++
 Для C++ VSPackage мастер поддерживает команды меню, окна инструментов и специальные редакторы. Искать его в **новый проект** диалоговое окно в **Visual C++ / расширяемости**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Ссылочные сборки VS SDK с помощью NuGet
 Для улучшенной портативности и совместного использования проектов расширения среды можно использовать версии NuGet ссылочных сборок пакета SDK для VS. Эти сборки можно найти на [nuget.org](http://www.nuget.org) опубликованное [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) и можно легко добавить в проект или решение с помощью Visual Studio **ссылается на и управление ими Пакеты NuGet** диалоговое окно. Можно добавить отдельные ссылки на сборки расширяемость для конкретного или добавить VS SDK ссылается на сборки, одновременно с помощью пакета SDK для VS [метапакет](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Дополнительные сведения о NuGet см. в разделе [документации по NuGet](/NuGet) и [пользовательский Интерфейс диспетчера пакетов](/NuGet/Tools/Package-Manager-UI) разделы.

 При использовании версии NuGet ссылочных сборок пакета SDK для VS, другому пользователю не нужно установить пакет SDK для VS для открытия и сборки проекта.  NuGet ссылочных сборок и средства сборки пакета SDK для VS будет автоматически устанавливаться на компьютере для этого проекта.

 Шаблоны элементов VS SDK используйте NuGet для их ссылки и средства сборки, поэтому вы получаете преимущества NuGet по умолчанию.

> [!NOTE]
>  Вы можете использовать ссылочные сборки установлен пакет SDK для VS с проектами (расположенный в \<расположение установки Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) и существующие проекты расширения среды не обязательно должны быть обновлен для использования пакетов NuGet.  Проект **ссылается на / добавить ссылку на** диалогового окна будет продолжать использовать ссылочные сборки установлен пакет SDK для VS.
>
>  Если вы хотите изменить существующие проекты для использования NuGet, см. в разделе [как: Миграция пакетов VSPackage в Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) которого имеется раздел об обновлении проектов расширяемости в пакеты NuGet.

## <a name="light-bulbs"></a>Лампочки
 Один из самых замечательных новых способов написания кода для расширения предоставляется в проекте Roslyn. Дополнительные сведения см. в разделе [Roslyn](https://github.com/dotnet/Roslyn).

 Лампочки являются новой возможностью, которая поставляется с VSSDK. Они являются значков, используемых в редакторе Visual Studio, которые разворачиваются для отображения набора действий рефакторинга кода или исправления для проблем, обозначенных в анализаторы встроенный код. Дополнительные сведения см. в разделе [Пошаговое руководство: Отображение предложений лампочки](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Руководство по работе обновленный пользователь
 Разработка новых расширений и компонентов для Visual Studio? Ознакомьтесь с обновленной и развернутом [рекомендации по пользовательскому интерфейсу Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Вы найдете [цвет маркеров](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [размеры шрифтов](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [спецификации макет диалогового окна](../extensibility/ux-guidelines/layout-for-visual-studio.md)и другие инструкции, необходимые легко интегрировать новый пользовательский Интерфейс с помощью Visual Studio.