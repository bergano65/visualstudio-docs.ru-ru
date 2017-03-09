---
title: "Тип &quot;&lt;имя_типа&gt;&quot; не может использоваться в атрибуте, так как его контейнер &quot;&lt;имя_контейнера&gt;&quot; не объявлен как &quot;Public&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31517"
  - "vbc31517"
helpviewer_keywords: 
  - "BC31517"
ms.assetid: 3d1a8f41-8652-4e37-a6bd-40b0ad306c6f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; не может использоваться в атрибуте, так как его контейнер &quot;&lt;имя_контейнера&gt;&quot; не объявлен как &quot;Public&quot;
Класс или модуль, в котором определен этот атрибут, не объявлен с использованием модификатора `Public`. Классы и модули, для которых не указан модификатор доступа, по умолчанию объявляются как `Friend`.  
  
 **Идентификатор ошибки:** BC31517  
  
### Исправление ошибки  
  
1.  Добавьте модификатор `Public` к классу или модулю, в котором определен этот атрибут.  
  
## См. также  
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)