---
title: "Ошибка компилятора CS0171 | Microsoft Docs"
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
  - "CS0171"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0171"
ms.assetid: 8c1d76c9-1048-4579-9031-23e3566e6288
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0171
Резервное поле для автоматически реализуемого свойства "имя" должно быть полностью назначено до возврата управления в вызывающий объект. Рассмотрите возможность вызова конструктора по умолчанию из инициализатора конструктора.  
  
 Конструктор в [структуре](/dotnet/csharp/language-reference/keywords/struct) должен инициализировать все поля структуры. Для получения дополнительной информации см. [Конструкторы](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 Следующий пример приводит к возникновению ошибки CS0171:  
  
```  
// CS0171.cs struct MyStruct { MyStruct(int initField)   // CS0171 { // i = initField;      // uncomment this line to resolve this error } public int i; } class MyClass { public static void Main() { MyStruct aStruct = new MyStruct(); } }  
```