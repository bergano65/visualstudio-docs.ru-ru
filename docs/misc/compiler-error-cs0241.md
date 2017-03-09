---
title: "Ошибка компилятора CS0241 | Microsoft Docs"
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
  - "CS0241"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "значения параметров метода по умолчанию"
  - "значения по умолчанию, значения параметров"
  - "значения по умолчанию, значения параметров метода"
  - "значения параметров по умолчанию"
  - "CS0241"
ms.assetid: be31b194-3de5-4aab-b23a-6cf790f940ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0241
Спецификаторы параметров по умолчанию не разрешены  
  
 [Параметры метода](/dotnet/csharp/language-reference/keywords/method-parameters) не могут иметь значения по умолчанию. Если вы хотите получить тот же эффект, используйте перегрузки метода. Дополнительные сведения см. в разделе [Передача параметров](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Пример  
 В следующем примере возникает ошибка CS0241. Кроме того, пример показывает, как с помощью перегрузки метода имитировать метод с аргументами по умолчанию.  
  
```  
// CS0241.cs public class A { public void Test(int i = 9) {}   // CS0241 } public class B { public void Test() { Test(9); } public void Test(int i)  {} } public class C { public static void Main() { B x = new B(); x.Test(); } }  
```