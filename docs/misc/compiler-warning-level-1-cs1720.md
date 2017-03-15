---
title: "Предупреждение компилятора (уровень 1) CS1720 | Microsoft Docs"
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
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS1720
Выражение всегда будет вызывать System.NullReferenceException, поскольку значение "универсальный\_тип" по умолчанию равно null  
  
 Если вы записали выражение с переменной универсального типа, имеющей значение по умолчанию, которая является ссылочным типом \(например, класс\), возникнет эта ошибка. Рассмотрим следующее выражение:  
  
```  
default(T).ToString()  
```  
  
 Так как `T` является ссылочным типом, его значение по умолчанию равно null, и поэтому попытка применить к нему метод <xref:System.Object.ToString%2A> вызовет <xref:System.NullReferenceException>.  
  
## Пример  
 Ограничение ссылки на класс для типа `T` гарантирует, что `T` является ссылочным типом.  
  
 При компиляции следующего примера будет выдано предупреждение CS1720.  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```