---
title: "Ошибка компилятора CS0021 | Microsoft Docs"
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
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0021
Не удается применить индексирование через \[\] к выражению типа "тип"  
  
 Попытка доступа к значению через индексатор для типа данных, который не поддерживает [Индексаторы](/dotnet/csharp/programming-guide/indexers/index).  
  
 Ошибка CS0021 может возникнуть при попытке использовать индексатор в сборке C\+\+. В этом случае оформите класс C\+\+ с помощью атрибута `DefaultMember`, чтобы компилятор C\# знал, какой из индексаторов используется по умолчанию. Следующий пример приводит к возникновению ошибки CS0021.  
  
## Пример  
 Этот файл компилируется в DLL\-файл — с закомментированным атрибутом `DefaultMember` — для создания ошибки.  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## Пример  
 Ниже приведен файл C\#, который вызывает DLL\-файл. Этот файл пытается получить доступ к классу через индексатор, но так как никакой член не был объявлен как индексатор по умолчанию, возникает ошибка.  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```