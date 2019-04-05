---
title: Элемент Icon (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de31652af7bc3fd2da3c5e67e37df8e9ff120e8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991938"
---
# <a name="icon-element-visual-studio-templates"></a>Элемент Icon (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает путь и имя файла, файла образа, который служит в качестве значок, который отображается в либо **новый проект** или **Добавление нового элемента** диалоговом окне для шаблона.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Значок >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Icon>  
    IconFileName  
</Icon>  
```  
  
```  
<Icon Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Package`|Необязательный атрибут для сложных пользовательских скриптов.<br /><br /> Идентификатор GUID, указывающий пакет Visual Studio.|  
|`ID`|Необязательный атрибут для сложных пользовательских скриптов.<br /><br /> Указывает идентификатор ресурса Visual Studio.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным, если `Package` и `ID` используются атрибуты.  
  
 Текст предоставляет путь и имя файла значка шаблона, который будет отображаться в **новый проект** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `Icon` — обязательный дочерний элемент элемента `TemplateData`.  
  
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
