---
title: "Общие сведения о перегрузке | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "перегрузка функций, о перегрузке функции"
  - "перегрузку операторов, о перезагрузке оператора"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Общие сведения о перегрузке
Язык C\+\+ позволяет перегружать функции и операторы. Перегрузка — это предоставление нескольких определений для некоторого имени функции в одной области действия. Компилятор выбирает требуемую версию функции или оператора в зависимости от аргументов, содержащихся в вызове. Например, функция max считается перегруженной функцией. Ее можно использовать в коде так, как показано ниже:  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 При первом вызове функции, в котором запрашивается максимальное значение двух переменных типа `int`, вызывается функция `max( int, int )`. Однако при втором вызове функции аргументы имеют тип `double`, поэтому вызывается функция `max( double, double )`.  
  
## См. также  
 [Перегрузка \(C\+\+\)](../misc/overloading-cpp.md)