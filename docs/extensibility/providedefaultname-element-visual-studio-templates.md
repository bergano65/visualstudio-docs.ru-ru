---
title: "Элемент ProvideDefaultName (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords: ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48dbc92687a813dcd2a99659b9c2a8cc26129c79
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Элемент ProvideDefaultName (шаблоны Visual Studio)
Указывает ли [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] система проектов будет создавать имя по умолчанию для шаблона в **Добавление нового элемента** или **новый проект** диалоговое окно.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть либо `true` или `false`, указывающее, требуется ли создавать имя по умолчанию для шаблона в **Добавление нового элемента** или **новый проект** диалоговое окно.  
  
## <a name="remarks"></a>Примечания  
 `ProvideDefaultName` — это необязательный элемент. Значение по умолчанию — `true`.  
  
 Если `ProvideDefaultName` элемент `false`, **имя** поля в **Добавление нового элемента** и **новый проект** диалоговые окна содержат значение `<Enter_name>`.  
  
 Используйте [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) элемент, чтобы задать имя по умолчанию для проекта или элемента в **Добавление нового элемента** и **новый проект** диалоговым окнам.  
  
## <a name="example"></a>Пример  
 В следующем примере кода `ProvideDefaultName` элемент `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)