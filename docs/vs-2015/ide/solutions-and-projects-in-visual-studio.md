---
title: Проекты и решения
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.savedeferredsaveprojectonclose
- vs.untrustedtemplateopeningdocuments
- Project Properties.FullPath
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.getopenfilename
- vs.addnewitem
- vs.encoding
- vs.addexistingitem
- Project Properties.URL
- VS.SolutionExplorer
- Project Properties.FileName
- SolutionProperties.Name
- VS.SaveChangesDlg
- vs.newproject
- VS.SolutionExplorer.Selection
- SolutionProperties.Path
- vs.getdirectoryname
- vs.addexistingsolutionitem
- SolutionProperties.Description
- vs.environment.solutions
- vs.saveordiscarddeferredsaveproject
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- vs.solutionpropertypages
- vs.solutionpropertypages.startupproject
- vs.solutionpropertypages.configurationsettings
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- workspaces
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- vs.solutionpropertypages.projectdependencies
- applications [Visual Studio]
- projects [Visual Studio], setting up
- miscellaneous files
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 32b2f33af3c34cf6245e511cbd54d6ce7cc3a2bd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795256"
---
# <a name="solutions-and-projects-in-visual-studio"></a>Решения и проекты в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании в Visual Studio приложения, веб-сайта, веб-приложения, скрипта, подключаемого модуля и т. д. вы начинаете с *проекта*. С логической точки зрения проект содержит все файлы исходного кода, значки, изображения, файлы данных и прочие элементы, которые будут скомпилированы в исполняемую программу или веб-сайт, а также все остальное, что необходимо для выполнения компиляции.  Проект также содержит все параметры компилятора и другие файлы конфигурации, которые могут потребоваться разным службам или компонентам, с которыми программа будет взаимодействовать.

 Фактически проект является XML-файлом (*.vbproj, \*.csproj, \*.vcxproj), который определяет иерархию виртуальных папок с путями ко всем элементам, которые он содержит, а также все параметры сборки. В Visual Studio файл проекта используется обозревателем решений для отображения содержимого и параметров проекта. При компиляции проекта подсистема MSBuild использует файл проекта для создания исполняемого файла. Вы можете также настроить проекты для создания выходных данных другого типа.

 С точки зрения логики и файловой системы проект содержится в рамках *решения*, которое может содержать один или несколько проектов вместе с информацией о сборке, параметрами окна Visual Studio и любыми прочими файлами, которые не связаны с каким-либо проектом. Фактически решение является текстовым файлом в собственном уникальном формате; его обычно не изменяют вручную.

 Решение включает связанный SUO-файл, в который входят параметры, предпочтения и сведения о конфигурации для каждого пользователя, работавшего над проектом.

 На следующей схеме показана связь между проектами и решениями, а также элементы, которые они логически содержат.

 ![Проекты и решения Visual Studio](../ide/media/vs2015-project-diagram.png "схема_проекта_vs2015")

 Вы можете также создать пользовательские шаблоны проектов и элементов. Дополнительные сведения см. в статье [Creating Project and Item Templates](../ide/creating-project-and-item-templates.md) (Создание шаблонов проектов и элементов).

## <a name="creating-new-projects"></a>Создание новых проектов
 Самый простой способ создать новый проект — начать с существующего шаблона проекта, который состоит из базового набора предварительно созданных файлов кода, файлов конфигурации, активов и параметров для создания приложения или веб-сайта определенного типа на конкретном языке программирования. Эти шаблоны отображаются в **диалоговом окне "Новый проект"**, если последовательно выбрать пункты **Файл | Создать | Проект** или **Файл | Создать | Веб-сайт** в главном меню. Дополнительные сведения см. в статьях [Создание решений и проектов](../ide/creating-solutions-and-projects.md) и [NIB Создание проектов из шаблонов](http://msdn.microsoft.com/7c36d86a-6b79-4480-8228-0f925f1204b2).

## <a name="managing-projects-in-solution-explorer"></a>Управление проектами в обозревателе решений
 После создания нового проекта вы используете **обозреватель решений** для просмотра проектов и решений, их связанных элементов, а также для управления ими. На следующем рисунке показан обозреватель серверов с решением C#, включающим два проекта.

 ![Обозреватель решений](../ide/media/vs2015-solution-explorer.png "обозреватель_решений_vs2015")

## <a name="in-this-section"></a>В этом разделе

-   [Создание решений и проектов](../ide/creating-solutions-and-projects.md)

-   [Добавление и удаление элементов проекта](../ide/adding-and-removing-project-items.md)

-   [Управление свойствами проектов и решений](../ide/managing-project-and-solution-properties.md)

-   [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)

-   [Свойства приложения](../ide/application-properties.md)

-   [Управление сборками и подписывание манифестов](../ide/managing-assembly-and-manifest-signing.md)

-   [Практическое руководство. Задание значка приложения (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)

-   [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)

-   [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)

## <a name="see-also"></a>См. также раздел
 [Интегрированная среда разработки Visual Studio](../ide/visual-studio-ide.md)
