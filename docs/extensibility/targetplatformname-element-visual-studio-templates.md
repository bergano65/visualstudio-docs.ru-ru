---
title: "TargetPlatformName - элемент (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# TargetPlatformName - элемент (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает платформу, для которой предназначен шаблон проекта. Этот элемент используется для указания на то, что шаблон проекта служит для создания приложений [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].  
  
## Синтаксис  
  
```xml  
<VSTemplate>  
    <TemplateData>   
        <TargetPlatformName> OperatingSystem</TargetPlatformName>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Указывает версию операционной системы, для которой предназначен шаблон проекта.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
## Заметки  
 Этот текст должен быть **Windows**.  
  
## Пример  
 В этом примере указывается, что шаблон проекта предназначен для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <TargetPlatformName>Windows</TargetPlatformName> <RequiredPlatformVersion>8</RequiredPlatformVersion> </TemplateData> <TemplateContent> </TemplateContent> </VSTemplate>  
```  
  
## См. также  
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)