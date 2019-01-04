---
title: TEXT_POSITION | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TEXT_POSITION
helpviewer_keywords:
- TEXT_POSITION structure
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bcd07f34fb790f593653547f94112bffce248c55
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941379"
---
# <a name="textposition"></a>TEXT_POSITION
Описывает расположение строк и столбцов в данном тексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagTEXT_POSITION {   
   DWORD dwLine;  
   DWORD dwColumn;  
} TEXT_POSITION;  
```  
  
```csharp  
public struct TEXT_POSITION {   
   public uint dwLine;  
   public uint dwColumn;  
};  
```  
  
## <a name="members"></a>Участники  
 dwLine  
 Индекс строки в исходном файле.  
  
 dwColumn  
 Смещение символа в строку.  
  
## <a name="remarks"></a>Примечания  
 Эта структура используется в [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) и [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры.  
  
 Эта структура заполняется с помощью вызова следующих методов:  
  
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)  
  
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)  
  
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)  
  
- [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)  
  
  Эта структура передается как параметр для следующих методов:  
  
- [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)  
  
- [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)  
  
- [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)  
  
- [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)  
  
- [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)   
 [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)   
 [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)