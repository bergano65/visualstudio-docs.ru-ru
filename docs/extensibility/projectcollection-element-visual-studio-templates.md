---
title: Элемент ProjectCollection (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87a2bd56522477e56c57b69e4b3b400c84d3b0a0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841256"
---
# <a name="projectcollection-element-visual-studio-templates"></a>Элемент ProjectCollection (шаблоны Visual Studio)
Указывает организацию и содержимое многопроектных шаблонов.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает проекта в многопроектном шаблоне.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Группирует проекты в многопроектных шаблонах.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Задает содержимое шаблона.|  
  
## <a name="remarks"></a>Примечания  
 Многопроектные шаблоны используются в качестве контейнера для двух или нескольких проектов. `ProjectCollection` Элемент используется для указания проектов содержат в шаблоне. Дополнительные сведения о многопроектных шаблонах см. в разделе [как: Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Пример  
 В этом примере показан простой корневой многопроектных *.vstemplate* файл. В этом примере шаблон содержит два проекта `My Windows Application` и `My Class Library`. Атрибут `ProjectName` элемента `ProjectTemplateLink` задает имя, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] назначает данному проекту. Если `ProjectName` атрибут не существует, имя *.vstemplate* файл используется в качестве имени проекта.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме для Visual Studio шаблон](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание многопроектных шаблонов](../ide/how-to-create-multi-project-templates.md)