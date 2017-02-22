---
title: "Элемент ButtonText | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элемент ButtonText (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, ButtonText"
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент ButtonText
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Это поле позволяет указать текст, отображаемый в разных меню. По умолчанию `ButtonText` элемент отображается в меню контроллеров.`ButtonText` Элемент становится значением по умолчанию, если другие текстовые поля остаются пустыми.`ButtonText` Элемент не может быть пустым, даже если указаны другие текстовые поля.  
  
## Синтаксис  
  
```  
<ButtonText>My Command</ButtonText>  
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
|[Элемент строки](../extensibility/strings-element.md)|Группирует текстовые элементы, такие как `ButtonText` и `CommandName`.|  
  
## Текстовое значение  
 Текстовое значение `ButtonText` элемент содержит текст, который отображается для элементов меню, комбинировать и другие элементы пользовательского интерфейса \(UI\), содержащих текст видимым.  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)