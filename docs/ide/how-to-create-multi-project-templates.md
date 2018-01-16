---
title: "Создание многопроектных шаблонов для Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 86952d3b742abf3b73b22e17d695717ca8dac9bd
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-create-multi-project-templates"></a>Практическое руководство. Создание многопроектных шаблонов

Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. Когда в диалоговом окне **Новый проект** создается проект, основанный на многопроектном шаблоне, каждый проект в шаблоне добавляется в решение.

Многопроектный шаблон содержит два или несколько шаблонов проектов с корневым шаблоном типа `ProjectGroup`.

Многопроектные шаблоны ведут себя иначе, чем шаблоны для одного проекта. Они имеют следующие уникальные характеристики:

- Отдельным проектам в многопроектном шаблоне невозможно назначить имена через диалоговое окно **Новый проект**. Вместо этого нужно использовать атрибут `ProjectName` элемента `ProjectTemplateLink` в VSTEMPLATE-файле, чтобы указать имя для каждого проекта.

- Многопроектные шаблоны могут содержать проекты для разных языков, но сам шаблон можно поместить только в одну категорию. Категория шаблона указывается в элементе `ProjectType` VSTEMPLATE-файла.

Многопроектный шаблон должен включать следующие элементы, сжатые в ZIP-файл:

- Корневой VSTEMPLATE-файл для всего многопроектного шаблона. Этот корневой VSTEMPLATE-файл содержит метаданные, отображаемые в диалоговом окне **Новый проект**, а также указывает место для поиска VSTEMPLATE-файлов для проектов в этом шаблоне. Этот файл должен находиться в корне ZIP-файла.

- Две или более папок, содержащих файлы, которые нужны для завершения шаблона проекта. Сюда входят все файлы кода для проекта, а также VSTEMPLATE-файл.

Например, ZIP-файл многопроектного шаблона с двумя проектами может иметь следующие файлы и каталоги:

- MultiProjectTemplate.vstemplate
- \Project1\Project1.vstemplate
- \Project1\Project1.vbproj
- \Project1\Class.vb
- \Project2\Project2.vstemplate
- \Project2\Project2.vbproj
- \Project2\Class.vb

Корневой VSTEMPLATE-файл многопроектного шаблона отличается от однопроектного шаблона следующим образом:

- Атрибут `Type` элемента `VSTemplate` содержит значение `ProjectGroup`, а не `Project`. Пример:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- Элемент `TemplateContent` содержит элемент `ProjectCollection` с одним или несколькими элементами `ProjectTemplateLink`, которые определяют пути к файлам VSTEMPLATE для включенных проектов. Пример:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\Project1.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\Project2.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

## <a name="to-create-a-multi-project-template-from-an-existing-solution"></a>Создание многопроектного шаблона из существующего решения

1. Создайте решения и добавьте два или более проектов.

1. Настройте проекты для экспорта в шаблон.

1. В меню **Проект** выберите пункт **Экспорт шаблона**.

   Открывается **мастер экспорта шаблонов**.

1. На странице **Выбор типа шаблона** выберите **Шаблон проекта**. Выберите проект, который необходимо экспортировать в шаблон, а затем нажмите кнопку **Далее**.

1. На странице **Выбор параметров шаблона** введите имя шаблона и необязательное описание, значок и рисунок предварительного просмотра для шаблона. Нажмите кнопку **Готово**.

   Проект будет экспортирован в ZIP-файл и помещен в указанное выходное расположение.

   > [!NOTE]
   > Каждый проект необходимо отдельно экспортировать в шаблон, поэтому повторите предыдущие шаги для каждого проекта в решении.

1. Создайте каталог для шаблона, содержащий вложенный каталог для каждого проекта.

1. Извлеките содержимое ZIP-файла каждого проекта в соответствующий созданный вложенный каталог.

1. В базовом каталоге создайте XML-файл с расширением **VSTEMPLATE**. Этот файл содержит метаданные для многопроектного шаблона. Пример структуры файла приведен ниже. Укажите относительный путь к VSTEMPLATE-файлу каждого проекта.

1. Выберите базовый каталог и в контекстном меню выберите пункты **Отправить** > **Сжатая ZIP-папка**.

   Файлы и папки сжимаются в ZIP-файл.

1. Скопируйте ZIP-файл в пользовательский каталог шаблона проекта. По умолчанию это каталог %USERPROFILE%\Documents\Visual Studio \<версия\>\Templates\ProjectTemplates.

1. В Visual Studio откройте диалоговое окно **Новый проект** и убедитесь, что в нем отображается шаблон.

## <a name="two-project-example"></a>Пример для двух проектов

В этом примере показан простой корневой VSTEMPLATE-файл, включающий несколько проектов. В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`. Атрибут `ProjectName` элемент `ProjectTemplateLink` указывает имя, которое задано проекту.

> [!TIP]
> Если атрибут `ProjectName` не указан, в качестве имени проекта используется имя VSTEMPLATE-файла.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example-with-solution-folders"></a>Пример с папками решений

В этом примере используется элемент `SolutionFolder`, чтобы разделить проекты на две группы — `Math Classes` и `Graphics Classes`. Шаблон содержит четыре проекта, два из которых размещаются в отдельных папках решения.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также

[Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)  
[Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)  
[Справочник по схемам шаблонов Visual Studio (расширяемость)](../extensibility/visual-studio-template-schema-reference.md)  
[Элемент SolutionFolder (шаблоны Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)  
[Элемент ProjectTemplateLink (шаблоны Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
