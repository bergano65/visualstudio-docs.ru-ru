---
title: "__sealed | Microsoft Docs"
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
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed - ключевое слово [C++]"
  - "__sealed - ключевое слово"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  Этот раздел относится только к управляемым расширениям для C\+\+ версии 1. Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В разделе [запечатанные](/visual-cpp/windows/sealed-cpp-component-extensions) сведения об использовании эквивалентную функциональность в новом синтаксисе.  
  
 Запрещает переопределение метода или использование класса в качестве базового класса.  
  
## Синтаксис  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## Заметки  
 Ключевое слово `__sealed` указывает, что метод класса невозможно переопределить или что класс не может быть базовым классом.  
  
 При использовании ключевого слова `__sealed` учитывайте следующее.  
  
-   Виртуальный метод `__sealed` невозможно переопределить.  
  
-   Если невиртуальный метод члена отмечается как `__sealed`, квалификация `__sealed` игнорируется.  
  
-   Метод `__sealed` не может быть чистым.  
  
-   **\_\_Sealed** ключевое слово не допускается при использовании [\_\_interface](/visual-cpp/cpp/interface) ключевое слово.  
  
 Если класс \(или структура\) отмечается как `__sealed`, класс невозможно использовать в качестве базового класса. Например:  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  Не разрешается использовать ключевое слово `__sealed` с ключевым словом `__abstract`.  
  
## Пример  
 В следующем примере объявляется запечатанный виртуальный метод \(`f`\). Затем функция переопределяется в `main()`, вызывая ошибку компилятора.  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```