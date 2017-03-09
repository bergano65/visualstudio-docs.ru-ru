---
title: "Ошибка компилятора CS1954 | Microsoft Docs"
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
  - "CS1954"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1954"
ms.assetid: bdec399e-c43d-46d3-a01b-ef3572786fe5
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS1954
Наиболее подходящий перегруженный метод, соответствующий method для элемента инициализатора коллекции, нельзя использовать. Методы Add инициализатора коллекции не могут иметь параметры ref или out.  
  
 Для инициализации класса коллекции с помощью инициализатора коллекции этот класс должен иметь `public` метод `Add`, не являющийся параметром `ref` или `out`.  
  
### Исправление ошибки  
  
-   Если вы можете изменить исходный код класса коллекции, предоставьте метод `Add`, который не принимает параметр `ref` или `out`.  
  
-   Если класс коллекции изменить нельзя, инициализируйте его с помощью конструкторов, которые он предоставляет. С ним нельзя использовать инициализатор коллекции.  
  
## Пример  
 В следующем примере создается ошибка CS1954, поскольку единственная доступная перегрузка метода `Add`, перечисленного в `MyList`, имеет параметр `ref`.  
  
```  
// cs1954.cs using System.Collections.Generic; class MyList<T> : IEnumerable<T> { List<T> _list; public void Add(ref T item) { _list.Add(item); } public System.Collections.Generic.IEnumerator<T> GetEnumerator() { int index = 0; T current = _list[index]; while (current != null) { yield return _list[index++]; } } System.Collections.IEnumerator System.Collections.IEnumerable.GetEnumerator() { return GetEnumerator(); } } public class MyClass { public string tree { get; set; } } class Program { static void Main(string[] args) { MyList<MyClass> myList = new MyList<MyClass> { new MyClass { tree = "maple" } }; // CS1954 } }  
  
```  
  
## См. также  
 [Инициализаторы объектов и коллекций](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)