---
title: Элемент EnableEditOfLocationField (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4363d5317e3b07f8d32c754336eeed04ec3ced5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037971"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>Элемент EnableEditOfLocationField (шаблоны Visual Studio)
Указывает, если пользователь может редактировать поле расположения.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<EnableEditOfLocationField >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Нет  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть либо `true` или `false`, указывающее, может ли пользователь изменять **расположение** текстовое поле в **новый проект** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `EnableEditOfLocationField` — это необязательный элемент. Значение по умолчанию — `true`, что позволяет пользователю изменять значения в **расположение** текстовое поле в **новый проект** диалоговое окно.  
  
 В **новый проект** диалоговом окне **расположение** текстовое поле указывает каталоге, где сохранен проект.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableEditOfLocationField>false</EnableEditOfLocationField>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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