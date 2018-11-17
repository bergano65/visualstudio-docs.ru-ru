---
title: TEXT_POSITION | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TEXT_POSITION
helpviewer_keywords:
- TEXT_POSITION structure
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d3e332b6081031b75e8398fa1883253347b5543
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809705"
---
# <a name="textposition"></a>TEXT_POSITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает расположение строк и столбцов в данном тексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

