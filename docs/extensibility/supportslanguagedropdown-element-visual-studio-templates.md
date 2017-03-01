---
title: "Элемент SupportsLanguageDropDown (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 10
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
ms.openlocfilehash: c5d2043ec03eb26d9327c59323f008bc9cd9ed2b
ms.lasthandoff: 02/22/2017

---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Элемент SupportsLanguageDropDown (шаблоны Visual Studio)
Указывает, является ли шаблон веб-элемента идентичным для нескольких языков и ли **язык** включен параметр **Add New Item** диалоговое окно.  
  
 \<VSTemplate настроек  
 \<TemplateData настроек  
 \<SupportsLanguageDropDown настроек  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Текст должен быть либо `true` или `false`, указывая, ли **язык** доступен из **Add New Item** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `SupportsLanguageDropDown` — это необязательный элемент. Значение по умолчанию — `false`.  
  
 `SupportsLanguageDropDown` Элемент доступен только для шаблонов веб-элементов.  
  
 Если присвоено значение для этого элемента `true`, то шаблон элемента идентичен для всех языков программирования и **язык** будет включен параметр **Добавление нового элемента** диалоговое окно. Этот параметр позволяет выбрать язык программирования нового элемента, который требуется создать из шаблона.  
  
## <a name="example"></a>Пример  
 В следующем примере задается для отображения **языка** раскрывающийся список параметров.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
