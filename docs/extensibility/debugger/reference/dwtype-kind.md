---
title: dwTYPE_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d350b429b86c9ab3082816605c4c79e56982bb5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988236"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Указывает, как интерпретировать тип [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 TYPE_KIND_METADATA  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) объединения должны интерпретироваться как [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) структуры.  
  
 TYPE_KIND_PDB  
 `TYPE_INFO` Объединения должны интерпретироваться как [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) структуры.  
  
 TYPE_KIND_BUILT  
 `TYPE_INFO` Объединения должны интерпретироваться как [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) структуры.  
  
## <a name="remarks"></a>Примечания  
 Значения этого перечисления отображаются в `dwKind` поле [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структурировать и используются для определения интерпретации `type` члена объединения. `TYPE_INFO` Структура возвращается путем вызова [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)