---
title: "__nogc | Microsoft Docs"
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
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc type - объявление"
  - "классы [C++] неуправляемый тип"
  - "неуправляемые классы, объявление"
  - "неуправляемые классы"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  Этот раздел относится только к управляемым расширениям для C\+\+ версии 1. Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В новом синтаксисе нет необходимости явно отмечать тип как неуправляемый.  
  
 Явное объявление неуправляемого типа.  
  
## Синтаксис  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## Заметки  
 Ключевое слово `__nogc` служит для явного указания того, что объект выделяется в стандартной куче C\+\+. Это ключевое слово можно опустить. Если ключевое слово `__gc` или `__nogc` перед объявлением класса не указано, по умолчанию используется `__nogc`.  
  
 Объекты этого типа похожи на стандартные объекты C\+\+ тем, что они выделяются из стандартной кучи C\+\+ и не подвержены ограничениям управляемого объекта.  
  
 Ключевое слово `__nogc` используется также при явном выделении объекта типа \_\_value в стандартной куче C\+\+:  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  Ключевое слово `__nogc` можно также применять для типов массива и указателя.  
  
 Указатель gc не может быть членом класса `__nogc`. Инструкции по внедрению типа значения в классе `__nogc` см. в разделе [\_\_value](../misc/value.md).  
  
## Пример  
 В следующем примере объявляется неуправляемый класс \(`X`\) и создается и изменяется экземпляр объекта.  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**