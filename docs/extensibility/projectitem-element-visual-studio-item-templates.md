---
title: "Элемент ProjectItem (шаблоны элементов Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> - элемент [шаблоны элементов Visual Studio]"
  - "ProjectItem - элемент [шаблоны элементов Visual Studio]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент ProjectItem (шаблоны элементов Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает файла, который включается в шаблон элемента.  
  
> [!NOTE]
>  Элемент `ProjectItem` принимает различные атрибуты в зависимости от того, для чего предназначен шаблон \(для проекта или элемента\).  В этом разделе объясняется использование элемента `ProjectItem` для элементов.  Описание элемента `ProjectItem` для шаблонов проектов содержится в разделе [Элемент ProjectItem \(шаблоны проектов Visual Studio\)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
## Синтаксис  
  
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
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`SubType`|Необязательный атрибут.<br /><br /> Указывает подтип элемента в многофайловом шаблоне элемента.  Это значение используется для определения редактора, который [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет использовать, чтобы открыть элемент.|  
|`CustomTool`|Необязательный атрибут.<br /><br /> Пользовательский инструмент для элемента в файле проекта.|  
|`ItemType`|Необязательный атрибут.<br /><br /> Тип элемента в файле проекта.|  
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Логическое значение, указывающее, имеются ли в элементе значения параметров, которые должны быть заменены при создании проекта из шаблона.  Значение по умолчанию — `false`.|  
|`TargetFileName`|Необязательный атрибут.<br /><br /> Указывает имя элемента, создаваемого из шаблона.  Этот атрибут полезен при использовании замены параметров для создания имени элемента.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Строка `string`, представляющая имя файла в ZIP\-файле шаблона.  
  
## Заметки  
 `ProjectItem` является необязательным дочерним элементом `TemplateContent`.  
  
 Атрибут `TargetFileName` можно использовать для переименования файлов с параметрами.  Например, если файл `MyFile.vb` находится в корневом каталоге ZIP\-файла шаблона, но его необходимо переименовать, основываясь на имени файла, предоставленном пользователем в диалоговом окне **Добавить новый элемент**, нужно использовать следующий XML\-код.  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 При создании элемента из этого шаблона имя файла будет основываться на имени, введенном пользователем в диалоговом окне **Добавить новый элемент**.  Это может быть полезно при создании многофайловых шаблонов элементов.  Дополнительные сведения см. в разделах [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md) и [Параметры шаблона](../ide/template-parameters.md).  
  
## Пример  
 В следующем примере демонстрируются метаданные для стандартного шаблона элемента класса [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
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
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Практическое руководство. Создание многофайловых шаблонов элементов](../ide/how-to-create-multi-file-item-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)