---
title: "Ковариация массивов | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "массивы [C++], ковариация"
ms.assetid: 889fdde3-85fe-44d5-bf2d-d3d4aa14e746
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mithom"
manager: "douge"
---
# Ковариация массивов
Если ссылочный класс D с прямой или косвенный базовый класс B, массив типа D могут быть назначены переменной массива типа б.  
  
```  
// clr_array_covariance.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   // String derives from Object  
   array<Object^>^ oa = gcnew array<String^>(20);  
}  
```  
  
## Заметки  
 Назначение элементу массива должны быть совместимы по назначению с динамический тип массива. Назначение элементу массива с несовместимый тип вызовет System::ArrayTypeMismatchException исключение.  
  
 Ковариация массивов не применяется к массивам значение типа класса. Например, массивы Int32 нельзя преобразовать в объект ^ массивы, даже через упаковки\-преобразования.  
  
## Пример  
  
```  
// clr_array_covariance2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct Base { int i; };  
ref struct Derived  : Base {};  
ref struct Derived2 : Base {};  
ref struct Derived3 : Derived {};  
ref struct Other { short s; };  
  
int main() {  
   // Derived* d[] = new Derived*[100];  
   array<Derived^> ^ d = gcnew array<Derived^>(100);  
  
   // ok by array covariance  
   array<Base ^> ^  b = d;  
  
   // invalid  
   // b[0] = new Other;  
  
   // error (runtime exception)  
   // b[1] = gcnew Derived2;  
  
   // error (runtime exception),  
   // must be "at least" a Derived.  
   // b[0] = gcnew Base;  
  
   b[1] = gcnew Derived;  
   b[0] = gcnew Derived3;  
}  
```  
  
## См. также  
 [Массивы](/visual-cpp/windows/arrays-cpp-component-extensions)