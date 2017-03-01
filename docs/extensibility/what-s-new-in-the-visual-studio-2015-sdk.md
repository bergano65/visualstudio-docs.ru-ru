---
title: "Новые возможности пакета SDK для Visual Studio 2015 г. | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Новые возможности пакета SDK для Visual Studio 2015 г.
Пакет SDK для Visual Studio содержит следующие новые и обновленные средства для Visual Studio 2015, обновить Visual Studio 2015 и Visual Studio 2017 г.  
  
## <a name="vs-2015-sdk-update-1"></a>Обновления пакета SDK для Visual STUDIO 2015 1  
 Обновление 1 содержит средства для расширения хорошо работают с цвет темы и службы образов в Visual Studio.  
  
 Эти разделы находятся под [VSSDK программы](../extensibility/internals/vssdk-utilities.md) раздела:  
  
-   [Цвет темы средства](../extensibility/internals/color-theming-tools.md) позволяют создавать и изменять пользовательские цвета для Visual Studio.  
  
-   [Средства обновления образа](../extensibility/internals/image-service-tools.md) позволяют работать с файлами манифеста изображений Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Новый способ добавления пакета Visual Studio SDK для Visual Studio  
 Начиная с Visual Studio 2015, не нужно отдельно загружать пакет SDK для Visual Studio. Вместо этого его можно установить в процессе обычной установки, или вы можете установить его позже. При открытии или создать решение VSIX Visual Studio попросит установить средства расширения Visual Studio. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Новые способы создания расширений  
 Начиная с пакета SDK для Visual Studio 2015, имеют различные параметры для создания расширения, в зависимости от того, какой язык программирования используется.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# и Visual Basic  
 Для C# и Visual Basic существует множество шаблонов элементов проектов, которые позволяют создавать VSPackages, команды меню, окна инструментов, редактор классификаторов, оформлений редактор и расширения поле редактора. Можно добавить одно или все из них для стандартного проекта VSIX. Дополнительные сведения:  
  
-   [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     Мастер VSPackage больше не создает расширения в C# или Visual Basic.  
  
### <a name="c"></a>C++  
 В C++ VSPackage мастер поддерживает команды меню, окна инструментов и специальные редакторы. Найдите его в **новый проект** диалоговое окно в **Visual C++ и расширяемость**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>VS SDK ссылочные сборки в NuGet  
 Для портативности и совместного использования проектов расширения можно использовать версии NuGet ссылочных сборок VS SDK.  Эти данные доступны на [nuget.org](http://www.nuget.org) опубликованное [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) и может быть легко добавлен в проект или решение с помощью Visual Studio **ссылается / управление пакетами NuGet** диалогового окна. Можно добавлять отдельные ссылки на сборки расширяемость для конкретного или добавить VS SDK ссылается на сборки, одновременно с помощью VS SDK [Meta пакета](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Дополнительные сведения о NuGet см. в разделе [NuGet Обзор](http://docs.nuget.org/) и [управление пакетами NuGet с помощью диалогового окна](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
 При использовании версии NuGet ссылочных сборок VS SDK, другой пользователь не требуется для установки VS SDK, чтобы открыть и строить проект.  NuGet ссылочных сборок и средства построения VS SDK будут автоматически установлены на компьютере для этого проекта.  
  
 Шаблоны элементов VS SDK с помощью NuGet для их ссылки и средства построения, чтобы воспользоваться преимуществами NuGet по умолчанию.  
  
> [!NOTE]
>  Можно продолжать использовать ссылочные сборки пакета VS SDK, установленная с проектами (расположенный в папке \<расположение установки Visual Studio настроек \ VSSDK\VisualStudioIntegration\Common\Assemblies) и существующие проекты расширения среды не обязательно должны быть обновлены для использования пакетов NuGet.  Проект **ссылки и добавить ссылку** диалогового окна будет продолжать использовать пакет VS SDK ссылочных сборок.  
>   
>  Если вы хотите изменить существующие проекты для NuGet см. в разделе [как: переход с Migrate VSPackages на Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) которого имеется раздел по обновлению проекты расширения среды на пакеты NuGet.  
  
## <a name="light-bulbs"></a>Лампочки  
 Один из наиболее интересных новых способы написания кода расширения обеспечивается Roslyn проекта. Дополнительные сведения см. в разделе [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Лампочки являются новой возможностью, которая поставляется с VSSDK. Они являются значков, используемых в редакторе Visual Studio, разверните для отображения набора действий рефакторинга кода или исправления для проблемы, выявленные анализаторами встроенный код. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение лампочки предложения](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Руководство по работе обновленный пользователь  
 Разработка новых расширений или компоненты для Visual Studio? Ознакомьтесь с обновленной и расширенный [Visual Studio техники](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Вы найдете [цвет маркеров](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [размеры шрифтов](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [спецификации макет диалогового окна](../extensibility/ux-guidelines/layout-for-visual-studio.md)и другие инструкции, необходимые для беспрепятственной интеграции новых пользовательского интерфейса с помощью Visual Studio.
