---
title: "Свойство &quot;&lt;имя_свойства&gt;&quot; не может быть объявлено как Default, так как оно переопределяет свойство в базовом &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot;, которое не является свойством по умолчанию | Microsoft Docs"
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
  - "bc30504"
  - "vbc30504"
helpviewer_keywords: 
  - "BC30504"
ms.assetid: af5d55b7-80bc-4085-8fcf-01d8acbe9290
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойство &quot;&lt;имя_свойства&gt;&quot; не может быть объявлено как Default, так как оно переопределяет свойство в базовом &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot;, которое не является свойством по умолчанию
Предпринята попытка объявить свойство `Default`, не являющееся допустимым объявлением, так как оно переопределяет свойство, которое не было объявлено как `Default` в базовом классе.  
  
 **Идентификатор ошибки:** BC30504  
  
### Исправление ошибки  
  
-   Удалите объявление `Default`.  
  
## См. также  
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)