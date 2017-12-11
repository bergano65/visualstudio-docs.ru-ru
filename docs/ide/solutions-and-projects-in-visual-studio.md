---
title: "Решения и проекты в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 10/5/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.addnewsolutionitem
- vs.environment.projects
- vs.openproject
- vs.addnewitem
- vs.addexistingitem
- VS.SolutionExplorer
- vs.newproject
- vs.addexistingsolutionitem
- vs.environment.solutions
- VS.SolutionExplorer.Solutions
helpviewer_keywords:
- solution items, folder in Solution Explorer
- solution items, shared
- solutions [Visual Studio]
- project items [Visual Studio], about project items
- solutions [Visual Studio], designing
- projects [Visual Studio]
- solutions [Visual Studio], projects and
- projects [Visual Studio], setting up
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ca3094b3bfe35381236798164fa18e58304bae3f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-and-projects-in-visual-studio"></a>Решения и проекты в Visual Studio
При создании в Visual Studio приложения, веб-сайта, подключаемого модуля и т. д. вы начинаете с *проекта*. С логической точки зрения проект содержит все файлы исходного кода, значки, изображения, файлы данных и прочие элементы, которые будут скомпилированы в исполняемую программу или веб-сайт, а также все остальное, что необходимо для выполнения компиляции. Проект также содержит все параметры компилятора и другие файлы конфигурации, которые могут потребоваться разным службам или компонентам, с которыми программа будет взаимодействовать.  

> [!NOTE]
>  Но использовать решения или проекты вовсе не обязательно. Можно просто открыть файлы в Visual Studio и начать редактирование кода. Просмотрите видео [Develop code in Visual Studio without projects or solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) (Разработка кода в Visual Studio без использования проектов и решений), чтобы узнать об этом больше.  

Файл проекта (VBPROJ, CSPROJ, VCXPROJ) представляет собой XML-файл, который определяет иерархию виртуальных папок с путями ко всем элементам в проекте. Он также содержит параметры сборки. Чтобы просмотреть содержимое файла проекта, можно выбрать в обозревателе решений имя проекта, а затем элемент **Выгрузить проект** в контекстном меню. После этого снова откройте контекстное меню и выберите **Изменить \<имя_проекта\>**.  

В Visual Studio файл проекта используется обозревателем решений для отображения содержимого и параметров проекта. При компиляции проекта подсистема MSBuild использует файл проекта для создания исполняемого файла. Вы также можете настроить проекты для создания выходных данных другого типа.  

С точки зрения логики и файловой системы проект находится внутри *решения*, которое может содержать один или несколько связанных проектов вместе с информацией о сборке, параметрами окна Visual Studio и любыми прочими файлами, которые не относятся к какому-либо конкретному проекту. Решение описывается текстовым файлом (SLN) в собственном уникальном формате; его обычно не изменяют вручную.  

Решение включает связанный *SUO*-файл, в который входят параметры, предпочтения и сведения о конфигурации для каждого пользователя, работавшего над проектом.  

 На следующей схеме показана связь между проектами и решениями, а также элементы, которые они логически содержат.  

 ![Проекты и решения Visual Studio](../ide/media/vside-project-diagram.png)  

## <a name="creating-new-projects"></a>Создание новых проектов  
 Самый простой способ создать проект — начать с шаблона проекта, который состоит из базового набора предварительно созданных файлов кода, файлов конфигурации, активов и параметров для создания приложения или веб-сайта определенного типа и на конкретном языке программирования. Эти шаблоны отображаются в диалоговом окне **Новый проект** или **Новый веб-сайт**, если последовательно выбрать пункты **Файл**, **Создать**, **Проект** или **Файл**, **Создать**, **Веб-сайт**. Дополнительные сведения см. в разделе [Создание проектов и решений](../ide/creating-solutions-and-projects.md).  

Вы можете также создать пользовательские шаблоны проектов и элементов. Дополнительные сведения см. в статье [Creating Project and Item Templates](../ide/creating-project-and-item-templates.md) (Создание шаблонов проектов и элементов).  

## <a name="managing-projects-in-solution-explorer"></a>Управление проектами в обозревателе решений  
 После создания нового проекта вы используете **обозреватель решений** для просмотра проектов и решений, их связанных элементов, а также для управления ими. На следующем рисунке показан обозреватель решений с решением C#, включающим два проекта.  

 ![Обозреватель решений](../ide/media/vs2015_solution_explorer.png "обозреватель_решений_vs2015")  

## <a name="in-this-section"></a>Содержание  

-   [Создание решений и проектов](../ide/creating-solutions-and-projects.md)  

-   [Добавление и удаление элементов проекта](../ide/adding-and-removing-project-items.md)  

-   [Управление свойствами проекта и решения](../ide/managing-project-and-solution-properties.md)  

-   [Управление ссылками в проекте](../ide/managing-references-in-a-project.md)  

-   [Свойства приложения](../ide/application-properties.md)  

-   [Управление подписыванием сборок и манифестов](../ide/managing-assembly-and-manifest-signing.md)  

-   [Практическое руководство. Задание значка приложения (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Настройка конкретной целевой версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>См. также  
 [Интегрированная среда разработки Visual Studio](../ide/visual-studio-ide.md)
