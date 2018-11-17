---
title: Назовите элемент (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Name
helpviewer_keywords:
- Name element [Visual Studio project templates]
ms.assetid: 48788dbf-7da0-4443-8061-aab966fc22c8
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62964708e4211e0d845808de13c5f907c4dbd4f2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725830"
---
# <a name="name-element-visual-studio-templates"></a>Элемент Name (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает имя шаблона, как оно отображается в **новый проект** или **Добавление нового элемента** диалоговое окно.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Имя >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Name> Template Name </Name>  
```  
  
```  
<Name Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`Package`|Необязательный атрибут для сложных пользовательских скриптов.<br /><br /> Идентификатор GUID, указывающий пакет Visual Studio.|  
|`ID`|Необязательный атрибут для сложных пользовательских скриптов.<br /><br /> Указывает идентификатор ресурса Visual Studio.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным, если `Package` и `ID` используются атрибуты.  
  
 Текст предоставляет имя шаблона.  
  
## <a name="remarks"></a>Примечания  
 `Name` — обязательный дочерний элемент элемента `TemplateData`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../includes/csprcs-md.md)] приложения.  
  
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

