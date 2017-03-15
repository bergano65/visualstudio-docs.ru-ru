---
title: "Предупреждение о соответствии CLS CLS01506 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS01506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01506"
ms.assetid: 030f1b81-1159-4057-9fee-8721a419a5d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Предупреждение о соответствии CLS CLS01506
Ограничение varargs не входит в CLS  
  
 Ограничение varargs не входит в спецификацию CLS.  Спецификацией предусматривается только стандартное соглашение об управляемых вызовах.  
  
 Дополнительные сведения о проверке соответствия спецификации CLS см. в разделе [CLS\-совместимые сборки](http://msdn.microsoft.com/ru-ru/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 В следующем объявлении функции \(с использованием языка ассемблера MSIL\) показано, как можно вызвать предупреждение CLS01506:  
  
```  
.method public instance vararg void  Method1() cil managed  
```  
  
 Чтобы устранить это предупреждение, удалите ключевое слово **vararg**:  
  
```  
.method public instance void  Method1() cil managed  
```