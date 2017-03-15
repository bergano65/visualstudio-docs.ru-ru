---
title: "Ошибки компилятора при реализации класса, производного от CObject | Microsoft Docs"
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
  - "компиляция исходного кода, классы, производные от CObject"
  - "ошибки [C++]"
  - "ошибки [C++], компилятор"
  - "класс CObject, ошибки компилятора для производных классов"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Ошибки компилятора при реализации класса, производного от CObject
Если реализуется класс, производный от `CObject`, и код написан таким образом, что необходим вызов конструктора копирования или оператора присваивания этого класса, могут возникать ошибки компилятора, подобные приведенным ниже.  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Воспроизвести эту проблему можно, скомпилировав код из подраздела "Пример кода" ниже.  
  
> [!NOTE]
>  Пример кода, приведенный в этом разделе, вызывает следующие сообщения об ошибках:  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Причина возникновения ошибок компилятора состоит в том, что в классе `CObject` в файле AFX.h объявляется закрытый конструктор копирования и закрытый оператор присваивания. Соответственно, для класса, производного от `CObject`, компилятор по умолчанию не создает конструктор копирования и оператор присваивания. Так как компилятор не находит объявления этих функций в классе, он выводит сообщения об ошибках.  
  
 Чтобы исключить такие ошибки компилятора, необходимо реализовать конструктор копирования и оператор присваивания для класса, производного от `CObject`. Это показано в коде, приведенном ниже. Если раскомментировать строки, указанные в примере кода, то ошибки перестанут возникать.  
  
## Пример кода  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## См. также  
 [Предупреждение компилятораs C4600 Through C4999](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)