---
title: "Ошибка компилятора CS0011 | Microsoft Docs"
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
  - "CS0011"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0011"
ms.assetid: 892553d7-a516-4631-84cd-94db5722c90d
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Ошибка компилятора CS0011
Не удается разрешить базовый класс или интерфейс "класс" в сборке "сборка", на которую ссылается тип "тип"  
  
 Класс, который был импортирован из файла с помощью **\/reference**, является производным от не найденного класса или реализует не найденный интерфейс. Это может произойти, если требуемая библиотека DLL не включена в компиляцию с помощью **\/reference**.  
  
 Дополнительные сведения см. в разделах [Add Reference Dialog Box](http://msdn.microsoft.com/ru-ru/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) и [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).  
  
## Пример  
  
```  
// CS0011_1.cs // compile with: /target:library public class Outer { public class B { } }  
```  
  
## Пример  
 Второй файл создает библиотеку DLL, которая определяет класс `C`, производный от класса `B`, созданного в предыдущем примере.  
  
```  
// CS0011_2.cs // compile with: /target:library /reference:CS0011_1.dll // post-build command: del /f CS0011_1.dll public class C : Outer.B {}  
```  
  
## Пример  
 Третий файл заменяет библиотеку DLL, созданную на первом шаге, и пропускает определение внутреннего класса `B`.  
  
```  
// CS0011_3.cs // compile with: /target:library /out:cs0011_1.dll public class Outer {}  
```  
  
## Пример  
 Наконец, четвертый файл ссылается на класс `C`, определенный во втором примере, являющийся производным от класса `B`, который в данный момент отсутствует.  
  
 Следующий пример приводит к возникновению ошибки CS0011.  
  
```  
// CS0011_4.cs // compile with: /reference:CS0011_1.dll /reference:CS0011_2.dll // CS0011 expected class M { public static void Main() { C c = new C(); } }  
```  
  
## См. также  
 [Add Reference Dialog Box](http://msdn.microsoft.com/ru-ru/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)   
 [\/reference \(Import Metadata\)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option)