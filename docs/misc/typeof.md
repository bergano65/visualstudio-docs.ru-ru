---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof - ключевое слово"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**Примечание** Этот раздел относится только к версии 1 статьи "Управляемые расширения для C\+\+". Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В разделе [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) сведения об использовании эквивалентную функциональность в новом синтаксисе.  
  
 Возвращает **System::Type** заданного типа.  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 Здесь:  
  
 *typename*  
 Имя управляемого типа, для которого требуется имя **System::Type**. Обратите внимание, что в управляемой программе некоторые собственные типы являются псевдонимами типов среды CLR. Например, `int` является псевдонимом для **System::Int32**.  
  
## Заметки  
 Оператор **\_\_typeof** позволяет получить тип **System::Type** для указанного типа. Оператор **\_\_typeof** также можно использовать для возврата значения **System::Type** в блоке настраиваемых атрибутов. Дополнительные сведения о создании собственных атрибутов см. в разделе [attribute](/visual-cpp/windows/attribute).  
  
## Пример  
 В следующем примере настраиваемый атрибут \(`AtClass`\) применяется к классу \_\_gc \(`B`\). Затем значение настраиваемого атрибута извлекается с помощью оператора **\_\_typeof**:  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## Вывод  
  
```  
in Type * constructor  
AtClass  
```