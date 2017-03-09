---
title: "Ошибка компилятора CS1643 | Microsoft Docs"
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
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1643
Не все ветви кода возвращают значение в метод типа "тип"  
  
 Эта ошибка возникает, если в теле делегата отсутствует оператор return или имеется оператор return, который компилятор не может проверить. В следующем примере компилятор не пытается предсказать результат условия ветвления для проверки того, что блок анонимного метода всегда возвращает значение.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки CS1643:  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```