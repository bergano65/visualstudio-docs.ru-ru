---
title: "Комментарий XML содержит тег с атрибутом cref &quot;&lt;атрибут&gt;&quot;, который не удается найти | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Комментарий XML содержит тег с атрибутом cref &quot;&lt;атрибут&gt;&quot;, который не удается найти
Комментарий XML содержит тег с атрибутом cref "\<атрибут\>", который не удалось разрешить. Комментарий XML будет пропущен.  
  
 Теги могут иметь атрибут `cref`, который назначает ссылку на другой элемент XML путем указания относительного имени идентификатора. Во время компиляции компилятор заменяет значение, указанное пользователем, на квалифицированный идентификатор XML. Для поиска типа или члена компилятор использует обычные правила разрешения.  
  
 **Идентификатор ошибки:** BC42309  
  
### Исправление ошибки  
  
-   Проверьте атрибут `cref`, чтобы он указывал на допустимый элемент кода.  
  
## См. также  
 [Практическое руководство. Создание XML\-документации](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML\-теги для комментариев](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)