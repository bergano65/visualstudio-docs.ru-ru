---
title: "Ошибка компилятора CS0313 | Microsoft Docs"
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
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0313
Тип "тип1" нельзя использовать в качестве параметра типа "имя параметра" в универсальном типе или методе "тип2". Допускающий значение NULL тип "тип1" не удовлетворяет ограничению "тип2". Допускающие значение NULL типы не могу отвечать никаким ограничениям интерфейса.  
  
 Типы, допускающие значение NULL, не являются эквивалентными аналогичным типам, не допускающим этого значения. В представленном ниже примере структура `ImplStruct` удовлетворяет ограничению `BaseInterface`, однако структура `ImplStruct?` этому ограничению не удовлетворяет, так как метод `Nullable<ImplStruct>` не реализует интерфейс `BaseInterface`.  
  
### Исправление ошибки  
  
1.  Одно из решений показано в представленном ниже примере кода: определите обычную структуру `ImplStruct` в качестве первого аргумента типа в вызове метода `TestMethod`. Затем измените метод `TestMethod`, чтобы создать допускающую значение NULL версию структуры `Implstruct` в его операторе return.  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## Пример  
 Следующий код приводит к возникновению ошибки CS0313:  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## См. также  
 [Типы, допускающие значения NULL](/dotnet/csharp/programming-guide/nullable-types/index)