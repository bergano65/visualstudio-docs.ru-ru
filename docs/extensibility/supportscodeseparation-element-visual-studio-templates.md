---
title: Элемент SupportsCodeSeparation (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e669cf01f7becde7fa95af602ce4518bbaf6957e
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561396"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>Элемент SupportsCodeSeparation (шаблоны проектов Visual Studio)
Указывает ли **поместить код в отдельном файле** "флажок" включена в **Добавление нового элемента** диалоговое окно.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SupportsCodeSeparation >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
 Отсутствует.  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как отображается ли он в категорию шаблона и **новый проект** или **новый элемент** диалоговое окно.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть либо `true` или `false`, указывающее, ли **поместить код в отдельном файле** "флажок" включена в **Добавление нового элемента** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `SupportsCodeSeparation` — это необязательный элемент. Значение по умолчанию — `false`.  
  
 `SupportsCodeSeparation` Элемент доступен только для веб-шаблонов элементов.  
  
 Разделение кода, или модель страницы с выделенным кодом позволяет поместить разметку в один файл и программный код в другом файле. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и другими языками .NET использовать эту модель.  
  
## <a name="example"></a>Пример  
 В следующем примере задается для отображения **поместить код в отдельном файле** параметр.  
  
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
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
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