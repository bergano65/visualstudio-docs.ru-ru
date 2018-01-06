---
title: "Элемент ProjectSubType (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 11effbe7e1fc6c7380ba8dbc8da3f2fe14614b5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Элемент ProjectSubType (шаблоны Visual Studio)
Классифицирует шаблон в подкатегорию значения, указанного в `ProjectType` элемент.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Это значение задает подкатегорию шаблона.  
  
## <a name="remarks"></a>Примечания  
 `ProjectSubType` — необязательный дочерний элемент элемента `TemplateData`.  
  
 `ProjectSubType` Элемент предоставляет подкатегорию для [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) элемента. Это значение может включать:  
  
-   `SmartDevice-NETCFv1`: Указывает, что предназначен шаблон [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 1.0.  
  
-   `SmartDevice-NETCFv2`: Указывает, что целевые объекты tempalate [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 2.0.  
  
 Если шаблон содержит `ProjectType` элемент со значением `Web`, `ProjectSubType` элемент указывает язык программирования шаблона. Этот элемент может иметь следующие значения:  
  
-   `CSharp`: Указывает, что этот шаблон создает [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] веб-проекта или элемента.  
  
-   `VisualBasic`: Указывает, что этот шаблон создает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] веб-проекта или элемента.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения для устройств [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [Элемент ProjectType (шаблоны Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)