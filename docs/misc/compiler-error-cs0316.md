---
title: "Ошибка компилятора CS0316 | Microsoft Docs"
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
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0316
Имя параметра "имя" конфликтует с автоматически созданным именем параметра.  
  
 Зарезервированные слова не могут использоваться в качестве имен параметров. В следующем примере `value` является зарезервированным словом в контексте метода доступа индексатора или свойства по умолчанию.  
  
### Исправление ошибки  
  
1.  Измените имя параметра.  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0316:  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## См. также  
 [Индексаторы](/dotnet/csharp/programming-guide/indexers/index)   
 [Ключевые слова C\#](/dotnet/csharp/language-reference/keywords/index)