---
title: Элемент NumberOfParentCategoriesToRollUp (шаблоны Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93cbde61c4030a53819f42c65fca386174ac57d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036034"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>Элемент NumberOfParentCategoriesToRollUp (шаблоны Visual Studio)
Указывает количество родительских категориях, которые будут отображаться в **новый проект** диалоговое окно.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Элемент NumberOfParentCategoriesToRollUp >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml
<NumberOfParentCategoriesToRollUp>  
1  
</NumberOfParentCategoriesToRollUp>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 `integer` Значение является обязательным.  
  
 Это значение указывает количество родительских категориях, которые будут отображаться в **новый проект** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `NumberOfParentCategoriesToRollUp` — это необязательный элемент.  
  
## <a name="example"></a>Пример  
 В этом примере показаны метаданные для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows. Если шаблон с этими метаданными помещается двухуровневые папки ниже верхнего уровня [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] узел, шаблон будет отображаться в узле верхнего уровня в **новый проект** диалоговое окно. Если `NumberOfParentCategoriesToRollUp` не задано, шаблон появляется только в узле в котором он расположен физически.
  
```xml
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>  
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
 [Справочник по схеме для Visual Studio шаблон](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)