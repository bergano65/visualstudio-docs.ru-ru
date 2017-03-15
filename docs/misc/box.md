---
title: "__box | Microsoft Docs"
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
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box - зарезервированное слово"
  - "упаковка"
  - "распаковка"
  - "Упаковка-преобразование, __box-зарезервированное слово"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  Этот раздел относится только к управляемым расширениям для C\+\+ версии 1. Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В разделе [Упаковка\-преобразование](/visual-cpp/windows/boxing-cpp-component-extensions) сведения об использовании эквивалентную функциональность в новом синтаксисе.  
  
 Создает управляемую копию объекта класса \_\_value.  
  
## Синтаксис  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## Заметки  
 Ключевое слово `__box` используется для создания управляемого объекта \(производного от **System::ValueType**\) из существующего объекта класса \_\_value. Если применить ключевое слово `__box` к классу \_\_value, произойдет следующее.  
  
-   Управляемый объект выделяется в куче среды CLR.  
  
-   Текущее значение объекта класса \_\_value побитово копируется в управляемый объект.  
  
-   Возвращается адрес нового управляемого объекта.  
  
 Этот процесс называется упаковкой\-преобразованием. Это позволяет использовать любой объект класса \_\_value в универсальных подпрограммах, применимых для любого управляемого объекта, так как управляемый объект косвенно наследуется от **System::Object** \(поскольку **System::ValueType** наследуется от **System::Object**\).  
  
> [!NOTE]
>  Новый упакованный объект является копией объекта класса \_\_value. Поэтому изменения значения упакованного объекта не влияют на содержимое объекта класса \_\_value.  
  
## Пример  
 Ниже приведен пример упаковки\-преобразования и распаковки\-преобразования.  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 В следующем примере неуправляемый тип значения \(`V`\) упаковывается и передается в качестве управляемого параметра в функцию `Positive`.  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**