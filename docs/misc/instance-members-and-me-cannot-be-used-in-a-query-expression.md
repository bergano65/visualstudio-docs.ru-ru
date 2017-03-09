---
title: "Нельзя использовать члены экземпляра и &quot;Me&quot; в выражении запроса | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36535"
  - "bc36535"
helpviewer_keywords: 
  - "BC36535"
ms.assetid: afb5281b-70a7-48c7-a46d-39522b96b1ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Нельзя использовать члены экземпляра и &quot;Me&quot; в выражении запроса
Запрос LINQ в `Structure` содержит ссылку на `Me` или на член экземпляра структуры. Ссылки на `Me` или на члены экземпляра не допускаются в выражениях запроса в `Structure`.  
  
 **Идентификатор ошибки:** BC36535  
  
### Исправление ошибки  
  
1.  Создайте копию члена экземпляра или значения, возвращаемого по ссылке на `Me`, и используйте эту копию в выражении запроса, как показано в следующем примере.  
  
    ```vb#  
    Structure SampleStructure Public SearchValue As Integer Public Sub SetSearchValue(ByVal number As Integer) SearchValue = number End Sub Public Sub GetData() Dim sv = SearchValue Dim SampleData = New Integer() {1, 2, 3, 4} Dim query = From number In SampleData _ Where number < sv End Sub End Structure  
    ```  
  
## См. также  
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Me](http://msdn.microsoft.com/ru-ru/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)