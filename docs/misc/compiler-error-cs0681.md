---
title: "Ошибка компилятора CS0681 | Microsoft Docs"
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
  - "CS0681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0681"
ms.assetid: aa51ad94-df0a-481d-aaea-5b4291ebc41c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0681
Для полей модификатор "abstract" недопустим. Вместо него попробуйте использовать свойство  
  
 Поле нельзя сделать абстрактным. Однако можно иметь абстрактное свойство, которое получает доступ к полю.  
  
## Пример  
 В следующем примере происходит ошибка CS0681:  
  
```  
// CS0681.cs // compile with: /target:library abstract class C { abstract int num;  // CS0681 }  
  
```  
  
## Пример  
 Попробуйте вместо него использовать следующий код:  
  
```  
// CS0681b.cs // compile with: /target:library abstract class C { public abstract int num { get; set; } }  
```