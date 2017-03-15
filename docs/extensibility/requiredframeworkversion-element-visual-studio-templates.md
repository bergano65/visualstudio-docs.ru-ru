---
title: "Элемент RequiredFrameworkVersion (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<RequiredFrameworkVersion> (шаблоны Visual Studio)"
  - "RequiredFrameworkVersion (шаблоны Visual Studio)"
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Элемент RequiredFrameworkVersion (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает минимальную версию платформы .NET Framework, которая требуется для иерархии схемы шаблона.  
  
## Синтаксис  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон к какой\-либо категории и определяет, как он отображается в диалоговом окне **Создать проект** или **Добавить новый элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 В тексте необходимо указать самую низкую версию платформы .NET Framework, подходящую для этого шаблона.  
  
## Заметки  
 Элемент `RequiredFrameworkVersion` является необязательным.  Этот элемент используется, если шаблон поддерживает только определенную минимальную версию и более поздние версии .NET Framework, если таковые имеются.  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)