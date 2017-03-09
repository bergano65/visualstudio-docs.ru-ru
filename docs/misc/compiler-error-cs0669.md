---
title: "Ошибка компилятора CS0669 | Microsoft Docs"
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
  - "CS0669"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0669"
ms.assetid: c7f81869-79d7-481f-a026-2cef0e87df4c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0669
Класс с атрибутом ComImport не может иметь определенного пользователем конструктора.  
  
 Уровень COM\-взаимодействия в среде CLR предоставляет конструктор для классов [ComImport](frlrfSystemRuntimeInteropServicesComImportAttributeClassTopic). Следовательно, COM\-объект может использоваться в качестве управляемого объекта во время выполнения.  
  
 При компиляции следующего примера возникнет ошибка CS0669:  
  
```  
// CS0669.cs using System.Runtime.InteropServices; [ComImport, Guid("00000000-0000-0000-0000-000000000001")] class TestClass { TestClass()   // CS0669, delete constructor to resolve { } public static void Main() { } }  
```