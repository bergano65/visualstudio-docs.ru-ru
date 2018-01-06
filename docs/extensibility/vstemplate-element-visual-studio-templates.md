---
title: "Элемент VSTemplate (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords: VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c9fe87ae48c705e447b4fc5bd2834a417c4e8d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vstemplate-element-visual-studio-templates"></a>Элемент VSTemplate (шаблоны Visual Studio)
Содержит все метаданные шаблона проекта, шаблона элемента или начального набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|`Type`|Обозначает шаблон как шаблон проекта или шаблона элемента. Этот атрибут может иметь значение `Project` или `Item`.|  
|`Version`|Указывает номер версии для шаблона. Шаблоны в [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] и [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] имеют `Version` значение атрибута `3.0.0`.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Указывает данные, категорию шаблона и определяет его отображение в **новый проект** или **Добавление нового элемента** диалоговое окно.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Задает содержимое шаблона.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Необязательный элемент.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Необязательный элемент.|  
  
### <a name="parent-elements"></a>Родительские элементы  
 Отсутствует.  
  
## <a name="remarks"></a>Примечания  
 `VSTemplate` Элемент является корневым элементом VSTEMPLATE-файлов.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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