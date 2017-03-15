---
title: "DataKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DataKind - перечисление"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отображает заданную область значения.  
  
## Синтаксис  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elements  
 DataIsUnknown  
 Символ данных не может быть определено.  
  
 DataIsLocal  
 Элемент данных локальной переменной.  
  
 DataIsStaticLocal  
 Элемент данных статическая локальная переменная.  
  
 DataIsParam  
 Элемент данных формальный параметр.  
  
 DataIsObjectPtr  
 Элемент данных объекта \(указатель`this`\).  
  
 DataIsFileStatic  
 Элемент данных переменной файла\-scoped.  
  
 DataIsGlobal  
 Элемент данных глобальная переменная.  
  
 DataIsMember  
 Элемент данных, переменная члена объекта.  
  
 DataIsStaticMember  
 Элемент данных статическая переменная класса.  
  
 DataIsConstant  
 Элемент данных постоянное значение.  
  
## Заметки  
 В этом перечислении возвращаемые значения [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) метод.  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)