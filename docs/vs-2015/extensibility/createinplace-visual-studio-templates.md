---
title: CreateInPlace (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6973c73349a63eaf4e55c4b40fc71e6fc097c90d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571422"
---
# <a name="createinplace-visual-studio-templates"></a>CreateInPlace (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CreateInPlace (шаблоны Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/createinplace-visual-studio-templates).  
  
Указывает, следует ли создать проект и выполнить замену в указанном расположении, или выполнить замену во временном расположении и сохраните проект в указанное расположение.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<CreateInPlace >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<CreateInPlace> true/false </CreateInPlace>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть либо `true`, либо `false`. Если `true`, создается проект и выполняется замена параметров в расположении, указанном в **новый проект** диалоговое окно. Если `false`, выполняется замена параметров в во временную папку и проект копируется в указанное расположение.  
  
## <a name="remarks"></a>Примечания  
 `CreateInPlace` — это необязательный элемент. Значение по умолчанию — `true`.  
  
## <a name="example"></a>Пример  
 В следующем примере показаны метаданные для шаблона [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateInPlace>false</CreateInPlace>  
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
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

