---
title: "Элемент ProjectType (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d23be61b83cd3c62b6ab33a271968f500ad8ff81
ms.lasthandoff: 02/22/2017

---
# <a name="projecttype-element-visual-studio-templates"></a>Элемент ProjectType (шаблоны Visual Studio)
Относит шаблон проекта, чтобы он отображался в указанной группе в **новый проект** или **Add New Item** диалоговое окно.  
  
> [!WARNING]
>  Шаблоны проектов, поддерживаются для C++, начиная с версии Visual Studio 2012. Они не поддерживаются для C++ в Visual Studio 2010 и более ранних версий.  
  
 \<VSTemplate настроек  
 \<TemplateData настроек  
 \<ProjectType настроек  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
  
 Это значение указывает тип проекта шаблона будет создан и должно содержать одно из следующих значений:  
  
-   `CSharp`: Указывает, что этот шаблон создает [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта или элемента.  
  
-   `VisualBasic`: Указывает, что этот шаблон создает [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] проекта или элемента.  
  
-   `Web`: Указывает, что этот шаблон создает веб-проекта или элемента. Если `ProjectType` это значение содержится элемент, язык проект или элемент определен в [элемент ProjectSubType (шаблоны Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Примечания  
 `ProjectType` — обязательный дочерний элемент элемента `TemplateData`.  
  
 Значение `ProjectType` элемент указывает, когда шаблон находится в **новый проект** или **Add New Item** диалоговое окно. Например, шаблон с `ProjectType` значение `CSharp` отображается под **Visual C#** узел в **новый проект** диалоговое окно.  
  
 Подтип шаблона можно указать с помощью [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) элемента.  
  
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
 [Элемент ProjectSubType (шаблоны Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
