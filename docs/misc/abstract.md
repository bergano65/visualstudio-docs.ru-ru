---
title: "__abstract | Microsoft Docs"
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
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "абстрактные классы [C++]"
  - "__abstract - ключевое слово"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  Этот раздел относится только к управляемым расширениям для C\+\+ версии 1. Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В разделе [abstract](/visual-cpp/windows/abstract-cpp-component-extensions) сведения об использовании эквивалентную функциональность в новом синтаксисе.  
  
 Объявляет управляемый класс, не допускающий непосредственное создание экземпляров.  
  
## Синтаксис  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## Заметки  
 Ключевое слово `__abstract` объявляет, что целевой класс может использоваться только в качестве базового класса для другого класса. Применение модификатора `__abstract` к классу или структуре не означает, что результат является классом \_\_gc или структурой \_\_gc.  
  
 В отличие от понятия базового класса [abstract](/visual-cpp/cpp/abstract-classes-cpp) в языке C\+\+, класс с ключевым словом `__abstract` может определять свои функции\-члены.  
  
> [!NOTE]
>  Ключевое слово `__abstract` не допускается при использовании с ключевым словом `__value` или `__sealed` и является избыточным при использовании с ключевым словом `__interface`.  
  
## Пример  
 В следующем примере класс `Derived` является производным от абстрактного базового класса \(`Base`\). Затем предпринимается попытка создания экземпляров обоих классов, которая заканчивается успешно только для класса `Derived`.  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```