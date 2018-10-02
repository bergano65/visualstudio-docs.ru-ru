---
title: Элемент SupportsMasterPage (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6740145f280e28aca216ee298343bfa661ca5b48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564266"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>Элемент SupportsMasterPage (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент SupportsMasterPage (шаблоны Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/supportsmasterpage-element-visual-studio-templates).  
  
Указывает ли **выбрать главную страницу** устанавливается флажок на **Добавление нового элемента** диалоговое окно.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SupportsMasterPage >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Указывает данные, категорию шаблона и определяет, отображается ли он в **новый проект** или **новый элемент** диалоговое окно.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть либо `true` или `false`, указывающее, ли **выбрать главную страницу** устанавливается флажок на **Добавление нового элемента** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `SupportsMasterPage` — это необязательный элемент. Значение по умолчанию — `false`.  
  
 `SupportsMasterPage` Элемент доступен только для веб-шаблонов элементов.  
  
## <a name="example"></a>Пример  
 В следующем примере метаданные для веб-проекта, которая включает поддержку для главной страницы.  
  
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
        <SupportsMasterPage>true</SupportsMasterPage>  
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

