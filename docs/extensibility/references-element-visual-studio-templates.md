---
title: "Элемент References (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#References"
helpviewer_keywords: 
  - "<References> - элемент [шаблоны Visual Studio]"
  - "References - элемент [шаблоны Visual Studio]"
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Элемент References (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Группирует ссылки на сборки, которые добавляются шаблоном в проекты.  
  
## Синтаксис  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Задает ссылку на сборку, которая добавляется при добавлении элемента в проект.  В элементе `References` должен быть хотя бы один элемент `Reference`.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Задает содержимое шаблона.|  
  
## Заметки  
 `References` является необязательным дочерним элементом для `TemplateContent`.  
  
 Элементы `Reference` и `References` могут использоваться только в VSTEMPLATE\-файлах, атрибут `Type` которых имеет значение `Item`.  
  
## Пример  
 В следующем примере демонстрируется элемент `TemplateContent` шаблона элемента.  Этот XML добавляет ссылки на сборки System.dll и System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)