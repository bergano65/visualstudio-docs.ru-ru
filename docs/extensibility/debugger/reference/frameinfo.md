---
title: FRAMEINFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf77548136b941a4895e300e25612411611645dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958869"
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
  
## <a name="members"></a>Участники  
 m_dwValidFields  
 Сочетание флагов из [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) перечисление, указывающее, какие поля заполнены.  
  
 m_bstrFuncName  
 Имя функции, связанные с этим кадром стека.  
  
 m_bstrReturnType  
 Возвращаемый тип, связанный с этим кадром стека.  
  
 m_bstrArgs  
 Аргументы функции, связанные с этим кадром стека.  
  
 m_bstrLanguage  
 Язык, в котором функция реализована.  
  
 m_bstrModule  
 Имя модуля, связанный с этим кадром стека.  
  
 m_addrMin  
 Адрес минимальное физические стеки.  
  
 m_addrMAX  
 Адрес максимальное физические стеки.  
  
 m_pFrame  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий данный кадр стека.  
  
 m_pFrame  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , представляющий модуль, содержащий данный кадр стека.  
  
 m_fHasDebugInfo  
 Ненулевое значение (`TRUE`) Если отладочная информация содержится в заданный период.  
  
 m_fHasDebugInfo  
 Ненулевое значение (`TRUE`) Если кадр стека связана с кодом, который больше не является допустимым.  
  
 m_fHasDebugInfo  
 Ненулевое значение (`TRUE`) Если кадр стека имеет аннотации диспетчер отладки сеансов (SDM).  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) метод для заполнения. Эта структура также содержится в списке, который содержится в [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс, который, в свою очередь, возвращается из вызова [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)