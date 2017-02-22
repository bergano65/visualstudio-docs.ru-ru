---
title: "Элемент CustomParameter (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters - элемент [шаблоны проектов Visual Studio]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент CustomParameter (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит имя и значение пользовательского параметра, которые используются при создании проекта или элемента на основе шаблона.  
  
## Синтаксис  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Name`|Обязательное.  Имя параметра.  Формат параметра: $*name*$.|  
|`Value`|Обязательное.  Замещающее значение параметра.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Группирует пользовательские параметры, которые передаются мастеру шаблонов при выполнении мастером замены параметров.|  
  
## Заметки  
 Если шаблон содержит элементы `CustomParameter`, в каждом экземпляре атрибут `Name` заменяется атрибутом `Value` из файлов созданного проекта или элемента.  
  
## Пример  
 В следующем примере показано, как использовать в шаблоне несколько пользовательских параметров.  Когда проект или элемент создается из шаблона с использованием следующих пользовательских параметров, все экземпляры `$color1$` и `$color2$` в файлах шаблона заменяются на `Red` и `Blue` соответственно.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## См. также  
 [Элемент CustomParameters \(шаблоны Visual Studio\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)