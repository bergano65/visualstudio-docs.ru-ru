---
title: Элемент PromptForSaveOnCreation (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 99e26a5466dfeb08a927323d11f6ec49e53730c4
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53560588"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>Элемент PromptForSaveOnCreation (шаблоны Visual Studio)
Указывает, запрашивается ли пользователь в место сохранения проекта в **новый проект** диалоговое окно при создании проекта. Если этот элемент имеет значение `true`, то пользователю предлагается для сохранения расположения; Если `false`, то они не запрашиваются. (То есть будет создаваться временный проект.)  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<PromptForSaveOnCreation >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
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
  
 Этот текст должен быть либо `true` или `false`, `true` , указывающее, что пользователь будет запрашиваться для сохранения расположение при создании нового проекта.  
  
## <a name="remarks"></a>Примечания  
 `PromptForSaveOnCreation` — это необязательный элемент. Значение по умолчанию — `false`.  
  
 Временный проект — это проекты, которые можно создавать и изменять без сохранения содержимого проекта на диске.  
  
## <a name="example"></a>Пример  
 В следующем примере значение `PromptForSaveOnCreation` равным `false`, которое указывает, что проект может создаваться как временный проект.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>  
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
 [Справочник по схеме для Visual Studio шаблон](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)