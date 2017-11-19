---
title: "dwTYPE_KIND | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: dwTYPE_KIND
helpviewer_keywords: dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5207bbb9ff81a274d60ffb5957d2b5f31c73dbf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 Это перечисление отображаются в `dwKind` поле [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры и используются для определения интерпретации `type` члена объединения. `TYPE_INFO` Структура возвращается путем вызова [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) метод.  
  
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