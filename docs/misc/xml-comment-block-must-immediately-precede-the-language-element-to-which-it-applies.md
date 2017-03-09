---
title: "Блок комментариев XML должен находиться непосредственно перед элементом языка, к которому он применяется | Microsoft Docs"
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
  - "vbc42300"
  - "bc42300"
helpviewer_keywords: 
  - "BC42300"
ms.assetid: f9f7d1da-a723-4237-bd78-6db7ed8bc4aa
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Блок комментариев XML должен находиться непосредственно перед элементом языка, к которому он применяется
Блок комментариев XML должен находиться непосредственно перед элементом языка, к которому он применяется. XML\-комментарий будет игнорироваться.  
  
 Эта ошибка также возникает, если тег неправильно размещен или неправильно сформирован.  
  
 **Идентификатор ошибки:** BC42300  
  
### Исправление ошибки  
  
1.  Переместите блок комментариев перед элементом языка, к которому он применяется. Убедитесь, что перед начальным тегом не были случайно вставлены лишние знаки.  
  
2.  Убедитесь, что тег является допустимым.  
  
## См. также  
 [Практическое руководство. Создание XML\-документации](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML\-теги для комментариев](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)