---
title: "Элемент Folder (шаблоны проектов Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords: Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2c561564f75d4e5557c64f94adfb9caed6abce83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="folder-element-visual-studio-project-templates"></a>Элемент Folder (шаблоны проектов Visual Studio)
Указывает папку, в которые будут добавлены в проект.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<Папка >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательный атрибут.<br /><br /> Имя папки проекта.|  
|`TargetFolderName`|Необязательный атрибут.<br /><br /> Указывает имя, задаваемое папке при создании проекта из шаблона. Этот атрибут полезен при использовании замены параметров для создания имени папки или имени папки многоязыковой строки, не может использоваться непосредственно в ZIP-файл.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|`Folder`|Указывает папку для добавления в проект. `Folder`элементы могут содержать дочерние `Folder` элементов.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Задает файл для добавления в проект.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Проект](../extensibility/project-element-visual-studio-templates.md)|Необязательный дочерний элемент элемента [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Примечания  
 `Folder`Необязательный дочерний `Project`.  
  
 Для организации элементов проекта в папках в шаблоне можно использовать любой из следующих способов:  
  
-   Включить папки в ZIP-файл шаблона и добавить их в проект в VSTEMPLATE-файл, указав путь к файлу в `ProjectItem` элементы, которых не `Folder` элементов. Это рекомендуемый метод. Пример:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Включить папки в ZIP-файл шаблона и добавить их в проект в VSTEMPLATE-файл с `Folder` элементов. Пример:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Не включать папки в ZIP-файле шаблона, но Добавление папок с помощью `TargetFileName` атрибут `ProjectItem` элемента. Пример:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)