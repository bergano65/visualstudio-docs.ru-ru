---
title: "FRAMEINFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO"
helpviewer_keywords: 
  - "Структура FRAMEINFO"
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# FRAMEINFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает кадр стека.  
  
## Синтаксис  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```c#  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## Члены  
 m\_dwValidFields  
 Комбинация из пометит [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисление, которое определяет, какие поля заполняются.  
  
 m\_bstrFuncName  
 Имя функции, связанное с кадром стека.  
  
 m\_bstrReturnType  
 Возвращаемый тип, связанный с данным кадром стека.  
  
 m\_bstrArgs  
 Аргументы функции, связанные с кадром стека.  
  
 m\_bstrLanguage  
 Язык, на котором функция реализована.  
  
 m\_bstrModule  
 Имя модуля, связанное с кадром стека.  
  
 m\_addrMin  
 Минимальный физический адрес стека.  
  
 m\_addrMAX  
 Максимальный физический адрес стека.  
  
 m\_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) объект, представляющий этот кадр стека.  
  
 m\_pFrame  
 IDebugModule2 объект, представляющий модуль, содержащий этот кадр стека.  
  
 m\_fHasDebugInfo  
 Ненулевое значение \(`TRUE`если существует\) отладочной информации в данном фрейме.  
  
 m\_fHasDebugInfo  
 Ненулевое значение \(`TRUE`если кадр стека, связанный с кодом, который больше не является допустимым.  
  
 m\_fHasDebugInfo  
 Ненулевое значение \(`TRUE`если кадр стека дополняется сеанса отладки диспетчер \(SDM\).  
  
## Заметки  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) метод, который требуется заполнить.  Эта структура также содержится в списке, который содержится в [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс, который, в свою очередь, возвращается из вызова  [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)