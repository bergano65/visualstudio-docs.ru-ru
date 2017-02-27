---
title: "RequiredPlatformVersion - элемент (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# RequiredPlatformVersion - элемент (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает минимальную версию операционной системы, шаблон проекта необходима для правильной работы. Этот элемент используется для шаблонов проектов, которые создают [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложений.  
  
 `RequiredPlatformVersion` Значение сравнивается непосредственно с версией операционной системы. Если `RequiredPlatformVersion` выше, чем версия операционной системы, шаблон не отображается в **Новый проект** диалоговое окно. Чтобы указать шаблон для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии, установите `RequiredPlatformVersion` для 6.2.0. Чтобы указать шаблон для [!INCLUDE[win81](../debugger/includes/win81_md.md)] или RequiredPlatformVersion выше, задайте для 6.3.0.  
  
 Шаблоны `RequiredPlatformVersion`\= 8 совместимы с предыдущей клиента [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] шаблонов.  
  
 VSTemplate  
TemplateData  
…..TargetPlatformName  
RequiredPlatformVersion  
  
## Синтаксис  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## Атрибуты и элементы  
 Отсутствует.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Задает платформу, для которой предназначен шаблон проекта.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
## Заметки  
 Данный текст задает версии минимальной операционной системы, необходимых для шаблона.  
  
## Пример  
 В этом примере указывается, что шаблон проекта предназначен для [!INCLUDE[win8](../debugger/includes/win8_md.md)] или более поздней версии.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [TargetPlatformName \- элемент \(шаблоны Visual Studio\)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)