---
title: "CV_call_e | Microsoft Docs"
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
  - "CV_call_e - перечисление"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает соглашение о вызове функции.  
  
> [!NOTE]
>  Только самые распространенные значения перечисления описаны здесь.  Полное перечисление доступна в файле заголовка cvconst.h.  
  
## Синтаксис  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elements  
 CV\_CALL\_NEAR\_C  
 Определяет функция\-Позвоня о вызовах с помощью ближайшего справа налево принудительная.  Вызывающая функция очищает стек.  
  
 CV\_CALL\_NEAR\_FAST  
 Определяет функция\-Позвоня о вызовах с помощью ближайшего push слева направо с регистрами.  Вызываемая функция использует сумму байтов параметра для очистки стека.  
  
 CV\_CALL\_NEAR\_STD  
 Определяет функция\-Позвоня о вызовах с помощью ближайшего стандартный вызов push \(справа налево\).  
  
 CV\_CALL\_NEAR\_SYS  
 Определяет функция\-Позвоня о вызовах с помощью ближайшего системный вызов.  
  
 CV\_CALL\_THISCALL  
 Определяет соглашение с помощью функция\-Позвоня `this` вызов \(`this` указатель, передаваемый в регистр\).  
  
 CV\_CALL\_CLRCALL  
 Определяет функция\-Позвоня соглашение, используемое средой CLR \(известные также как управляемый код соглашения о вызовах\).  
  
## Заметки  
 Значения в этом перечислении возвращаемых вызовом [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) метод.  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)