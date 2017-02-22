---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "Перечисление EncUnavailableReason"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` Представляет причины, то  **"Операция ""Изменить и продолжить"""** не доступны.  
  
## Синтаксис  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```c#  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### Параметры  
 ENCUN\_NONE  
 Нет конкретной причины правка и кнопка продолжить не доступны.  
  
 ENCUN\_INTEROP  
 Правка и кнопка продолжить не доступны во время вызова метода Взаимодействия.  
  
 ENCUN\_SQLCLR  
 Правка и кнопка продолжить не доступны во время вызова процедуры SQL, использующий среду CLR.  
  
 ENCUN\_MINIDUMP  
 Правка и кнопка продолжить не доступны при обработке мини\-дамп.  
  
 ENCUN\_EMBEDDED  
 Правка и кнопка продолжить не доступны при обработке внедренный код.  
  
 ENCUN\_ATTACH  
 Правка и кнопка продолжить не доступны, поскольку сеанс был вложен в, не запущено, отладчик.  
  
 ENCUN\_WIN64  
 Правка и кнопка продолжить не доступны при обработке 64 \- код windows.  
  
## Заметки  
 Это перечисление только для внутреннего использования by [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) и  [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) такие методы, как реализуется пользовательским поставщиком порта должны всегда возвращать  `E_NOTIMPL`.  
  
## Требования  
 Заголовок: msdbg.idl  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)