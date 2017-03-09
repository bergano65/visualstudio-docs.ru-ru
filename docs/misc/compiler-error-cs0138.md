---
title: "Ошибка компилятора CS0138 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0138
Директива using namespace может применяться только к пространствам имен; "тип" является типом, а не пространством имен  
  
 Директива [using](/dotnet/csharp/language-reference/keywords/using) может принимать в качестве параметра только имя пространства имен. Для получения дополнительной информации см. [Пространства имен](/dotnet/csharp/programming-guide/namespaces/index).  
  
 При компиляции следующего примера возникнет ошибка CS0138:  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```