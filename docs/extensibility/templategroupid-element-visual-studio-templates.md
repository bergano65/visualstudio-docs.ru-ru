---
title: "Элемент TemplateGroupID (шаблоны Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> - элемент [шаблоны Visual Studio]"
  - "TemplateGroupID - элемент [шаблоны Visual Studio]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент TemplateGroupID (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает, в каком типе проекта будут отображаться шаблоны элементов.  Этот элемент действителен, когда для [ShowByDefault \(шаблоны Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) задано значение `false`.  Когда для [ShowByDefault \(шаблоны Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) задано значение `true`, шаблон элементов доступен во всех типах проектов.  
  
## Синтаксис  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст задает идентификатор для категории шаблонов элементов.  
  
## Заметки  
 `TemplateGroupID` является элементом.  
  
 Значение элемента `TemplateGroupID` используется вместе с регистрацией системы проектов \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<номер\_версии\>*\\Projects\\\) для фильтрации шаблонов, которые появляются в диалоговом окне **Добавление нового элемента**.  
  
|Значение Visual C\+\+|Значение|  
|---------------------------|--------------|  
|VC\-Native|Используется для собственных проектов.  Кроме того, используется по умолчанию, когда не удается определить тип проекта.|  
|VC\-Managed|Используется для управляемых проектов \(\/clr\).|  
|VC\-Windows|Используется для всех проектов, нацеленных на платформу Windows \(машинный код\/управляемый код\/хранилище\).|  
|WinRT\-Native\-UAP|Используется для проектов хранилища Windows 10.|  
|CodeSharing\-Native|Используется для общих проектов элементов.|  
|WinRT\-Native\-6.3|Используется для проектов Магазина Windows 8.1.|  
|WinRT\-Native\-Phone\-6.3|Используется для проектов Магазина Windows Phone 8.1.|  
|WinRT\-Native|Используется для проектов Магазина Windows 8.0.|  
|VC\-Android|Используется для проектов Android.|  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)