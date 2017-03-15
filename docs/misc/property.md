---
title: "__property | Microsoft Docs"
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
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property - ключевое слово"
  - "управляемые классы"
  - "классы управляемого свойства [C++]"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  Этот раздел относится только к управляемым расширениям для C\+\+ версии 1. Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В разделе [property](/visual-cpp/windows/property-cpp-component-extensions) сведения об использовании эквивалентную функциональность в новом синтаксисе.  
  
 Объявляет либо скалярное, либо индексированное свойство управляемого класса.  
  
## Синтаксис  
  
```  
  
__property  
function-declarator  
  
```  
  
## Заметки  
 Ключевое слово `__property` содержит объявление свойства и может использоваться в типе класса, интерфейса или значения. Свойство может иметь функцию получения свойства \(только чтение\), задания свойства \(только запись\) или обе этих функции \(чтение и запись\).  
  
> [!NOTE]
>  Имя свойства не может совпадать с именем управляемого класса, к которому оно относится. Функция получения свойства должна иметь тип, который совпадает с типом последнего параметра в соответствующей функции задания свойства.  
  
## Пример  
 В следующем примере к объявлению `Size` добавляется скалярное свойство `MyClass`. Затем это свойство явным образом получается и задается при помощи функций `get_Size` и `set_Size`:  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## Вывод  
  
```  
0  
4  
4  
```