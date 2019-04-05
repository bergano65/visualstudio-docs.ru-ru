---
title: Элемент TemplateContent (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe87bff62c1044442b579664fb789f918a2e6c2d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980436"
---
# <a name="templatecontent-element-visual-studio-templates"></a>Элемент TemplateContent (шаблоны проектов Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает содержимое шаблона.  
  
 \<VSTemplate >  
 \<TemplateContent >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Указывает, следует ли для построения решения при создании проекта из шаблона.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает организацию и содержимое многопроектных шаблонов.|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает, файлов или каталогов, добавляемых в проект.|  
|[Ссылки](../extensibility/references-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Задает ссылки на сборки, необходимые для шаблона элемента.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Необязательный элемент.<br /><br /> Указывает файл, который содержится в шаблоне.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает любые настраиваемые параметры, которые будут использоваться при создании проекта или элемента из шаблона.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблон элемента или комплект для начала работы.|  
  
## <a name="remarks"></a>Примечания  
 `TemplateContent` является обязательным элементом.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../includes/csprcs-md.md)] приложения.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
