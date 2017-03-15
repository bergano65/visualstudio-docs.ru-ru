---
title: "Недопустимая ссылка &lt;ссылка&gt; на дружественную сборку В объявлениях InternalsVisibleTo нельзя указывать версию, язык и региональные параметры, токен открытого ключа или архитектуру процессора. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Недопустимая ссылка &lt;ссылка&gt; на дружественную сборку В объявлениях InternalsVisibleTo нельзя указывать версию, язык и региональные параметры, токен открытого ключа или архитектуру процессора.
Имя сборки, передаваемое в конструктор атрибута <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, содержит атрибут `Version`, `Culture`, `PublicKeyToken` или `processorArchitecture`.  
  
 **Идентификатор ошибки:** BC31534  
  
### Исправление ошибки  
  
1.  Удалите атрибут `Version`, `Culture`, `PublicKeyToken` или `processorArchitecture` атрибут из имени сборки, передаваемой в конструктор атрибута <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
## См. также  
 <xref:System.Reflection.AssemblyName>   
 [НЕ В СБОРКЕ. Дружественные сборки \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/80e7a33a-ca91-450b-a00e-c5a7986e228c)