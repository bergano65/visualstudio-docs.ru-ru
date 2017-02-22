---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Конструктор классов поддерживает структуры C\+\+, которые объявлены с ключевым словом `struct`.  Например:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Дополнительные сведения об использовании типа `struct` см. в разделе [struct](/visual-cpp/cpp/struct-cpp).  
  
 Фигура структуры C\+\+ на схеме классов выглядит и работает подобно фигуре класса, за исключением того что метка читается как **Struct** и у структуры вместо скругленных квадратные углы.  
  
|Элемент кода|Представление конструктора классов|  
|------------------|----------------------------------------|  
|`struct StructureName {};`|**Имя структуры**<br /><br /> Структура|  
  
## См. также  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Классы и структуры](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)