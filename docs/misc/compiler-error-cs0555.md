---
title: "Ошибка компилятора CS0555 | Microsoft Docs"
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
  - "CS0555"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0555"
ms.assetid: e4b2f890-98b4-4578-b1de-ebaafc8b3da2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0555
Определенный пользователем оператор не может получить объект данного включающего типа и выполнить преобразование в объект данного включающего типа.  
  
 Пользовательские преобразования в значения включающего класса не допускаются; в операторе подобного типа нет необходимости.  
  
 В следующем примере возникает ошибка CS0555:  
  
```  
// CS0555.cs public class MyClass { // delete the following operator to resolve this CS0555 public static implicit operator MyClass(MyClass aa)   // CS0555 { return new MyClass(); } public static void Main() { } }  
```