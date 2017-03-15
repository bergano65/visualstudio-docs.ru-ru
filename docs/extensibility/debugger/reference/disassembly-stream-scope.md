---
title: "DISASSEMBLY_STREAM_SCOPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_STREAM_SCOPE"
helpviewer_keywords: 
  - "Перечисление DISASSEMBLY_STREAM_SCOPE"
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DISASSEMBLY_STREAM_SCOPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет область потока дизассемблированный код.  
  
## Синтаксис  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## Члены  
 DSS\_HUGE  
 Определяет то демонтируя контекст кода, созданного более вывода, чем клиент обычно хотел бы получить в одном вызове.  
  
 DSS\_FUNCTION  
 Указывает, что функция, которая содержит контекст кода должна быть демонтирована.  Указывает, что поток дизассемблированный код представляет функцию, возвращаемый [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) метод.  
  
 DSS\_MODULE  
 Возвращаемый `IDebugDisassemblyStream2::GetScope` метод определяет, что поток дизассемблированный код представляет модуль.  
  
 DSS\_ALL  
 Определяет разборку для всего адресного пространства.  
  
## Заметки  
 Передается в качестве аргумента [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) метод и возвращается  [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md) метод.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)