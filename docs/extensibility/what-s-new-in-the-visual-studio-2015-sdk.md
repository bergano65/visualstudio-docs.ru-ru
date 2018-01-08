---
title: "Какой &#39; новые возможности пакета SDK для Visual Studio 2015 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1008e1c81c6d99bc9fa0615263cf023a56101435
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Какой &#39; новые возможности Visual Studio 2015 SDK
Пакет SDK для Visual Studio имеет следующие новые и обновленные средства для Visual Studio 2015, Visual Studio 2015 обновлена и Visual Studio 2017 г.  
  
## <a name="vs-2015-sdk-update-1"></a>Обновление пакета SDK для VS 2015 1  
 Обновление 1 содержит инструменты для работы с цветовой темы и службы образов в Visual Studio расширения.  
  
 Эти разделы находятся в [VSSDK программы](../extensibility/internals/vssdk-utilities.md) раздела:  
  
-   [Цвет темы средства](../extensibility/internals/color-theming-tools.md) позволяют создавать и редактировать пользовательские цвета для Visual Studio.  
  
-   [Средства работы с образами службы](../extensibility/internals/image-service-tools.md) позволяют работать с файлами манифеста изображений Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Новый способ добавить пакет SDK для Visual Studio в Visual Studio  
 Начиная с Visual Studio 2015, не нужно отдельно загрузить пакет SDK для Visual Studio. Вместо этого его можно установить в процессе обычной процедуры установки, или вы можете установить его позже. При открытии или создайте решение VSIX Visual Studio попросит установить средства расширения Visual Studio. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Новые способы Создание расширений  
 Начиная с пакета SDK для Visual Studio 2015, есть вариантов для создания расширения, в зависимости от того, какой язык программирования, на который вы используете.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# и Visual Basic  
 Для C# и Visual Basic имеется полный набор шаблонов элементов проекта, которые позволяют создавать пакеты VSPackage, команды меню, окна инструментов, редактор классификаторы, оформления редактора и расширений поле редактора. Можно добавить любые или все из них для стандартного проекта VSIX. Дополнительные сведения:  
  
-   [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     Мастер VSPackage больше не создает расширения в C# или Visual Basic.  
  
### <a name="c"></a>C++  
 В C++ VSPackage мастер поддерживает команды меню, окна инструментов и пользовательских редакторов. Найдите его в **новый проект** диалогового окна в **Visual C++ и расширяемости**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK ссылочные сборки через NuGet  
 Для повышения переносимость и расширяемость проектов для управления доступом можно использовать NuGet версии ссылочных сборок VS SDK.  Они доступны на [nuget.org](http://www.nuget.org) опубликованное [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) и может быть легко добавлена в проект или решение в Visual Studio **ссылается / управление NuGet Пакеты** диалогового окна. Можно добавить отдельные ссылки на сборки расширяемость для конкретного или добавить VS SDK ссылается на сборки, одновременно с помощью пакета SDK для VS [Meta пакета](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Дополнительные сведения о NuGet см. в разделе [документации по NuGet](/NuGet) и [пользовательского интерфейса диспетчера пакетов](/NuGet/Tools/Package-Manager-UI) разделы.  
  
 При использовании NuGet версии ссылочных сборок VS SDK другому пользователю не нужно установить пакет SDK для VS для открытия и сборки проекта.  NuGet ссылочные сборки и средства построения VS SDK автоматически устанавливается на компьютере для этого проекта.  
  
 Шаблоны элементов VS SDK использовать NuGet для их ссылки и средства сборки, чтобы получить преимущества NuGet по умолчанию.  
  
> [!NOTE]
>  Можно продолжать использовать ссылочные сборки VS SDK, установленный с проектами (расположенный в \<расположение установки Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) и существующие проекты расширения не обязательно должны быть обновлен для использования пакетов NuGet.  Проект **ссылается на "/" Добавление ссылки** диалогового окна будет продолжать использовать ссылочные сборки установленный пакет SDK для VS.  
>   
>  Если вы хотите изменить существующие проекты для использования NuGet см. в разделе [как: переход с Migrate VSPackages на Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) содержит раздел на обновление расширяемости проектов на пакеты NuGet.  
  
## <a name="light-bulbs"></a>Лампочки  
 Одно из наиболее интересных новые способы написания кода в модуле обеспечивается Roslyn проекта. Дополнительные сведения см. в разделе [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Лампочки являются новой возможностью, которая поставляется с VSSDK. Они являются значков, используемых в редакторе Visual Studio, которые можно развернуть, чтобы отобразить набор действий рефакторинга кода или исправления для проблем, которые идентифицируют анализаторов встроенного кода. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение лампочки предложения](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Обновленные техники  
 Разработка новых расширений или компоненты для Visual Studio? Извлечь обновленные и развернутым [Visual Studio техники](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Вы найдете [цвета маркеров](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [размеры шрифтов](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [спецификации макет диалогового окна](../extensibility/ux-guidelines/layout-for-visual-studio.md)и другие рекомендации, необходимые для легко интегрировать нового пользовательского интерфейса с помощью Visual Studio.