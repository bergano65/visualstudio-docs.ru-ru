---
title: "Ошибка компилятора CS0273 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0273
Модификатор доступности функции доступа "метод\_доступа\_свойства" должен содержать более жесткие ограничения, чем свойство или индексатор "свойство"  
  
 Модификатор доступности метода доступа set или get должен быть более ограничивающим, чем свойство или индексатор "свойство\/индексатор".  
  
 Эта ошибка возникает при объявлении свойства или индексатора с модификатором доступа, который менее ограничивающий, чем модификатор доступа одного из его методов доступа. Для устранения этой ошибки используйте соответствующий модификатор доступа для свойства или метода доступа set. Дополнительные сведения см. в разделе [Доступность методов доступа](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Пример  
 В приведенном ниже примере содержится внутреннее свойство с внутренним методом set. Следующий пример приводит к возникновению ошибки CS0273:  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```