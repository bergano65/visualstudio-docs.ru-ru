---
title: "Элемент ProjectItem (шаблоны элементов Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2fe9abece45efdc206e775bc8f5e79666e334001
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="projectitem-element-visual-studio-item-templates"></a>Элемент ProjectItem (шаблоны элементов Visual Studio)
Указывает файл, который включен в шаблоне элемента.  
  
> [!NOTE]
>  `ProjectItem` Элемент принимает различные атрибуты в зависимости от того, является ли шаблон для проекта или элемента. В этом разделе объясняется `ProjectItem` элемент для элемента. Объяснение `ProjectItem` для шаблонов проектов см. в разделе [элемент ProjectItem (шаблоны проектов Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectItem >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`SubType`|Необязательный атрибут.<br /><br /> Указывает подтип элемента в шаблон элемента нескольких файлов. Это значение используется для определения редактора, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет использоваться для открытия элемента.|  
|`CustomTool`|Необязательный атрибут.<br /><br /> Задает инструмент для элемента в файле проекта.|  
|`ItemType`|Необязательный атрибут.<br /><br /> Задает тип элемента в файле проекта.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, содержит ли элемент значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию — `false`.|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Задает имя элемента, который создается из шаблона. Этот атрибут полезен при использовании замены параметров для создания имени элемента.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Объект `string` , представляющее имя файла в ZIP-файле шаблона.  
  
## <a name="remarks"></a>Примечания  
 `ProjectItem`Необязательный дочерний `TemplateContent`.  
  
 `TargetFileName` Атрибут можно использовать для переименования файлов с параметрами. Например если файл `MyFile.vb` существует в корневом каталоге ZIP-файл шаблона, но файл должен называться на основе имени файла, введенного пользователем в нужной **Добавление нового элемента** диалоговое окно, используется следующий XML-код:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Когда элемент создается на основе этого шаблона, имя файла будет основываться на имени, введенного пользователем в **Добавление нового элемента** диалоговое окно. Это полезно при создании многофайловых шаблонов элементов. Дополнительные сведения см. в разделе [как: создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md) и [параметров шаблона](../ide/template-parameters.md).  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется метаданные для стандартного шаблона элемента для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] класса.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)