---
title: "Слишком много приложений-клиентов DLL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Слишком много приложений-клиентов DLL
Библиотека динамической компоновки \(DLL\) для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] может обеспечить доступ ограниченному числу ведущих приложений. Ваше приложение и другие приложения, которые являются узлами [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] \(к некоторым из которых может обращаться ваше приложение\), пытаются получить доступ к библиотеке DLL [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] одновременно.  
  
### Исправление ошибки  
  
-   Уменьшите число открытых приложений, обращающихся к [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## См. также  
 [Типы ошибок](/dotnet/visual-basic/programming-guide/language-features/error-types)