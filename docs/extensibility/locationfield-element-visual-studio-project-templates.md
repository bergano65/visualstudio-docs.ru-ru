---
title: Элемент LocationField (шаблоны проектов Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0877d374317e3a7142996b012ff6abefc6b94724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Элемент LocationField (шаблоны проектов Visual Studio)
Указывает ли **расположение** текстовое поле в **новый проект** включено, отключено или скрытым для шаблона проекта диалоговое окно.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<LocationField >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон и определяет его отображения в любом **новый проект**.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Ниже перечислены допустимые текстовые значения  
  
-   `Enabled`, указывает, что **расположение** поле **новый проект** включен диалоговое окно.  
  
-   `Disabled`, указывает, что **расположение** поле **новый проект** диалоговое окно будет отключена.  
  
-   `Hidden`, указывает, что **расположение** поле **новый проект** диалоговое окно скрывается.  
  
## <a name="remarks"></a>Примечания  
 Значение по умолчанию — `Enabled`.  
  
 **Расположение** текстовое поле в **новый проект** диалоговое окно позволяет пользователям возможность изменить каталог по умолчанию, в котором сохраняются новые проекты.  
  
 Значение, указанное в `Location` элемент учитывается только в диалоговом окне Если базовая система поддерживает его.  
  
## <a name="example"></a>Пример  
 В следующем примере показаны метаданные для шаблона [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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