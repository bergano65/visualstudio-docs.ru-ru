---
title: "Элемент SolutionFolder (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder"
helpviewer_keywords: 
  - "<SolutionFolder> - элемент [шаблоны Visual Studio]"
  - "SolutionFolder - элемент [шаблоны Visual Studio]"
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Элемент SolutionFolder (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Группирует проекты в многопроектных шаблонах.  
  
## Синтаксис  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Name`|Обязательный атрибут.<br /><br /> Имя папки решения.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Задает путь к VSTEMPLATE\-файлу для одного проекта в многопроектном шаблоне.|  
|`SolutionFolder`|Необязательный элемент.<br /><br /> Группирует проекты в многопроектных шаблонах.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Указывает организацию и содержимое многопроектных шаблонов.|  
|`SolutionFolder`|Группирует проекты в многопроектных шаблонах.|  
  
## Заметки  
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов.  Элемент `SolutionFolder` используется для распределения проектов в шаблоне по группам.  Папки, указанные элементами `SolutionFolder`, создаются в виде папок решения в проекте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Дополнительные сведения о многопроектных шаблонах см. в разделе [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md).  
  
## Пример  
 В этом примере используется элемент `SolutionFolder`, чтобы разделить многопроектный шаблон на две группы — `Math Classes` и `Graphics Classes`.  Шаблон содержит четыре проекта, два из которых размещаются в отдельных папках решения.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
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
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)