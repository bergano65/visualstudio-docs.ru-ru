---
title: "Практическое руководство. Создание многопроектных шаблонов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "многопроектные шаблоны"
  - "шаблоны проектов, создание многопроектных шаблонов"
  - "шаблоны Visual Studio, создание многопроектных шаблонов"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Практическое руководство. Создание многопроектных шаблонов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов.  При создании проекта на основе многопроектного шаблона из диалогового окна **Создать проект** каждый проект в шаблоне добавляется в решение.  
  
 Многопроектный шаблон должен включать следующие элементы, сжатые в один ZIP\-файл.  
  
-   Корневой файл с расширением VSTEMPLATE для всего многопроектного шаблона.  Этот корневой файл с расширением VSTEMPLATE содержит метаданные, которые отображаются в диалоговом окне **Создать проект**, и указывает место поиска файлов с расширением VSTEMPLATE для проектов этого шаблона.  Этот файл должен быть расположен в корневом каталоге файла с расширением ZIP.  
  
-   Одну или несколько папок, содержащих файлы, необходимые для шаблона проекта.  Они включают все файлы с кодом проекта и файл с расширением VSTEMPLATE проекта.  
  
 Например, ZIP\-файл многопроектного шаблона с двумя проектами может иметь следующие файлы и каталоги.  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 Корневой файл с расширением VSTEMPLATE для многопроектного шаблона отличается от шаблона для одного проекта следующими параметрами.  
  
-   Атрибут `Type` элемента `VSTemplate` содержит значение `ProjectGroup`.  Примеры.  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   Элемент `TemplateContent` содержит элемент `ProjectCollection` с одним или несколькими элементами `ProjectTemplateLink`, которые определяют пути к файлам с расширением VSTEMPLATE включенных проектов.  Примеры.  
  
    ```  
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
  
 Многопроектные шаблоны работают другим образом, чем обычные шаблоны.  Многопроектные шаблоны имеют следующие уникальные характеристики:  
  
-   Отдельным проектам в многопроектном шаблоне не могут быть назначены имена в диалоговом окне **Новый проект**.  Вместо этого используйте атрибут `ProjectName` элемента `ProjectTemplateLink` для указания имени для каждого проекта.  Для получения дополнительных сведений см. первый пример в следующем разделе.  
  
-   Многопроектные шаблоны могут содержать проекты, написанные на разных языках, но весь шаблон может быть помещен только в одну категорию с помощью элемента `ProjectType`.  
  
### Чтобы создать многопроектный шаблон  
  
1.  Создайте проекты для включения в многопроектный шаблон.  
  
2.  Создайте файлы с расширением VSTEMPLATE для каждого проекта.  Дополнительные сведения см. в разделе [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md).  
  
3.  Создайте корневой файл с расширением VSTEMPLATE, который будет содержать метаданные для многопроектного шаблона.  Для получения дополнительных сведений см. первый пример в следующем разделе.  
  
4.  Выберите файлы и папки для включения в шаблон, щелкните их правой кнопкой мыши, выберите **Отправить**, затем щелкните **Сжатая ZIP\-папка**.  Файлы и папки, сожмутся в ZIP\-файл.  
  
5.  Поместите ZIP\-файл шаблона в каталог шаблонов проектов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  По умолчанию этот каталог \\Мои документы\\Visual Studio *номер версии*\\Templates\\ProjectTemplates\\.  
  
## Пример  
 В этом примере показан базовый, включающий несколько проектов корневой файл с расширением VSTEMPLATE.  В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`.  Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту.  Если атрибут `ProjectName` не существует, имя VSTEMPLATE\-файла используется в качестве имени проекта.  
  
```  
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
  
## Пример  
 В этом примере используется элемент `SolutionFolder` для разделения проектов на две группы `Math Classes` и `Graphics Classes`.  Шаблон содержит четыре проекта, два из которых расположены в отдельных папках решения.  
  
```  
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
  
## См. также  
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Элемент SolutionFolder \(шаблоны Visual Studio\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [Элемент ProjectTemplateLink \(шаблоны Visual Studio\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)