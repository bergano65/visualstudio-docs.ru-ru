---
title: "Элемент ProjectTemplateLink (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink"
helpviewer_keywords: 
  - "<ProjectTemplateLink> - элемент [шаблоны Visual Studio]"
  - "ProjectTemplateLink - элемент [шаблоны Visual Studio]"
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент ProjectTemplateLink (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает путь к VSTEMPLATE\-файлу для одного проекта в многопроектном шаблоне.  
  
## Синтаксис  
  
```  
<ProjectTemplateLink ProjectName="Name">     PathToTemplateFile </ProjectTemplateLink>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`ProjectName`|Необязательный атрибут.<br /><br /> Задает имя каждого отдельного проекта в многопроектном шаблоне.  Диалоговое окно **Создать проект** не может присваивать имена отдельным проектам.|  
|`CopyParameters`|Включает копирование всех переменных в шаблоне основной группы в каждый из связанных шаблонов.<br /><br /> Параметры в связанных шаблонах имеют префикс `"$ext_*$"`.  Например, если в шаблоне родительской группы параметр `$projectname$` имеет значение ExampleProject1, когда доходит очередь до выполнения связанного шаблона, он получает параметр `$ext_projectname$`, который является копией параметра `$projectname$` из шаблона родительской группы.<br /><br /> Это позволяет связанным шаблонам совместно использовать некоторые общие параметры, которые можно удобным образом создавать в шаблоне родительской группы.<br /><br /> Этот атрибут является необязательным и для него автоматически устанавливается значение по умолчанию `false`, если он не включен.<br /><br /> Представлено в обновлении 2 для Visual Studio 2013.  Сведения о правильной версии продукта см. в статье [Referencing Assemblies Delivered in the Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/ru-ru/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Указывает организацию и содержимое многопроектных шаблонов.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Группирует проекты в многопроектных шаблонах.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст указывает путь к VSTEMPLATE\-файлу шаблона.  
  
## Заметки  
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов.  Элемент `ProjectTemplateLink` используется для указания расположения VSTEMPLATE\-файла для одного или нескольких проектов шаблона.  VSTEMPLATE\-файл многопроектного шаблона содержит по одному элементу `ProjectTemplateLink` на каждый проект в шаблоне.  Дополнительные сведения о многопроектных шаблонах см. в разделе [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md).  
  
## Пример  
 В этом примере показан простой корневой VSTEMPLATE\-файл, включающий несколько проектов.  В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`.  Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту.  Если атрибут `ProjectName` не существует, имя VSTEMPLATE\-файла используется в качестве имени проекта.  
  
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
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)