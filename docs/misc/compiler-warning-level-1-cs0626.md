---
title: "Предупреждение компилятора (уровень 1) CS0626 | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Предупреждение компилятора (уровень 1) CS0626
Метод, оператор или метод доступа "метод" помечен как внешний и не имеет атрибутов. Для указания на внешнюю реализацию, возможно, следует добавить атрибут DllImport  
  
 Метод, помеченный `extern`, должен быть также помечен атрибутом, например атрибутом [DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic).  
  
 Атрибут указывает, где реализуется метод. Во время выполнения программе потребуется эта информация.  
  
 При компиляции следующего примера будет выдано предупреждение CS0626:  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```