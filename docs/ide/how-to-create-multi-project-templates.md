---
title: "Практическое руководство. Создание многопроектных шаблонов | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d4ffd6c3aa23ebc2b801de2d581876ff5afd480
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-multi-project-templates"></a>Практическое руководство. Создание многопроектных шаблонов
Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. Когда в диалоговом окне **Новый проект** создается проект, основанный на многопроектном шаблоне, каждый проект в шаблоне добавляется в решение.  
  
 Многопроектный шаблон должен включать следующие элементы, сжатые в ZIP-файл:  
  
-   Корневой VSTEMPLATE-файл для всего многопроектного шаблона. Этот корневой VSTEMPLATE-файл содержит метаданные, отображаемые в диалоговом окне **Новый проект**, а также указывает место для поиска VSTEMPLATE-файлов для проектов в этом шаблоне. Этот файл должен находиться в корне ZIP-файла.  
  
-   Одна или несколько папок, содержащих файлы, которые нужны для завершения шаблона проекта. Сюда входят все файлы кода для проекта, а также VSTEMPLATE-файл.  
  
 Например, ZIP-файл многопроектного шаблона с двумя проектами может иметь следующие файлы и каталоги:  
  
 MultiProjectTemplate.vstemplate  
  
 \Project1\Project1.vstemplate  
  
 \Project1\Project1.vbproj  
  
 \Project1\Class.vb  
  
 \Project2\Project2.vstemplate  
  
 \Project2\Project2.vbproj  
  
 \Project2\Class.vb  
  
 Корневой VSTEMPLATE-файл многопроектного шаблона отличается от однопроектного шаблона следующим образом:  
  
-   Атрибут `Type` элемента `VSTemplate` содержит значение `ProjectGroup`. Например:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   Элемент `TemplateContent` содержит элемент `ProjectCollection` с одним или несколькими элементами `ProjectTemplateLink`, которые определяют пути к файлам VSTEMPLATE для включенных проектов. Например:  
  
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
  
 Многопроектные шаблоны также ведут себя иначе, чем обычные шаблоны. Многопроектные шаблоны имеют следующие уникальные характеристики:  
  
-   Отдельным проектам в многопроектном шаблоне невозможно назначить имена через диалоговое окно **Новый проект**. Вместо этого нужно использовать атрибут `ProjectName` элемента `ProjectTemplateLink`, чтобы указать имя для каждого проекта. Дополнительные сведения см. в первом примере в следующем разделе.  
  
-   Многопроектные шаблоны могут содержать проекты, написанные на разных языках, но сам шаблон можно поместить только в одну категорию с помощью элемента `ProjectType`.  
  
### <a name="to-create-a-multi-project-template"></a>Создание многопроектного шаблона  
  
1.  Создайте проекты для включения в многопроектный шаблон.  
  
2.  Создайте VSTEMPLATE-файлы для каждого проекта. Дополнительные сведения см. в статье [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md).  
  
3.  Создайте корневой VSTEMPLATE-файл, который будет содержать метаданные для многопроектного шаблона. Дополнительные сведения см. в первом примере в следующем разделе.  
  
4.  Выберите включаемые в шаблон файлы и папки, щелкните выбранное правой кнопкой мыши, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**. Файлы и папки сжимаются в ZIP-файл.  
  
5.  Поместите ZIP-файл шаблона в каталог шаблонов проекта [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. По умолчанию это каталог \My Documents\Visual Studio *версия*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Пример  
 В этом примере показан простой корневой VSTEMPLATE-файл, включающий несколько проектов. В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`. Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту. Если атрибут `ProjectName` не существует, имя VSTEMPLATE-файла используется в качестве имени проекта.  
  
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
  
## <a name="example"></a>Пример  
 В этом примере используется элемент `SolutionFolder`, чтобы разделить проекты на две группы — `Math Classes` и `Graphics Classes`. Шаблон содержит четыре проекта, два из которых размещаются в отдельных папках решения.  
  
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
  
## <a name="see-also"></a>См. также  
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Элемент SolutionFolder (шаблоны Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [Элемент ProjectTemplateLink (шаблоны Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)