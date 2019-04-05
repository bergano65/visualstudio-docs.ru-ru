---
title: Элемент FullClassName (расширение мастера шаблонов Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6cd466a41c61da929e9acc1619f384a3621f9c0
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "59002035"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Элемент FullClassName (расширение мастера шаблонов Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Полное имя класса, который реализует `IWizard` интерфейс.  
  
 \<VSTemplate >  
 \<WizardExtension >  
 ...  
 \<FullClassName >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<FullClassName>ClassName</FullClassName>  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Содержит элементы регистрации для настройки мастера шаблонов.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Данный текст задает класс, реализующий `IWizard` интерфейс. Указанный класс должен существовать в сборка, заданная параметром [сборки](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) элемент.  
  
## <a name="remarks"></a>Примечания  
 `FullClassName` — обязательный дочерний элемент элемента `WizardExtension`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для стандартного шаблона проекта для [!INCLUDE[csprcs](../includes/csprcs-md.md)] приложения Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md)
