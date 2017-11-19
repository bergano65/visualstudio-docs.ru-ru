---
title: "FRAMEINFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FRAMEINFO
helpviewer_keywords: FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31f87c5261db32e19c9382d4d9cd95f4081cbe19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="frameinfo"></a>FRAMEINFO
Описывает кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
  
```csharp  
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
  
## <a name="members"></a>Члены  
 m_dwValidFields  
 Сочетание флагов из [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисления, которое указывает, какие поля заполнены.  
  
 m_bstrFuncName  
 Имя функции, связанные с этим кадром стека.  
  
 m_bstrReturnType  
 Возвращаемый тип, связанный с этим кадром стека.  
  
 m_bstrArgs  
 Аргументы функции, связанные с этим кадром стека.  
  
 m_bstrLanguage  
 Язык, в котором реализована функция.  
  
 m_bstrModule  
 Имя модуля, связанный с этим кадром стека.  
  
 m_addrMin  
 Минимальный стек физический адрес.  
  
 m_addrMAX  
 Адрес максимальное физических стека.  
  
 m_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий этим кадром стека.  
  
 m_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий модуль, содержащий этим кадром стека.  
  
 m_fHasDebugInfo  
 Не равно нулю (`TRUE`) Если существует отладочной информации в заданный интервал.  
  
 m_fHasDebugInfo  
 Не равно нулю (`TRUE`) Если кадр стека связана с кодом, который больше не действительна.  
  
 m_fHasDebugInfo  
 Не равно нулю (`TRUE`) Если кадр стека отмечена диспетчером сеанса отладки (SDM).  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) метод, чтобы быть заполнено. Эта структура также содержится в списке, который содержится в [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс, который в свою очередь, возвращается из вызова [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)