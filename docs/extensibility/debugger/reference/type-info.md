---
title: TYPE_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 610abe4bd01c47b09d6438508318e90a41f6802e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127400"
---
# <a name="typeinfo"></a>TYPE_INFO
Эта структура определяет различные виды информации о типа поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 dwKind  
 Значение из [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисления, определяющее способ интерпретации объединения.  
  
 type.typeMeta  
 [C++] Содержит [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) структуры, если `dwKind` — `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [C++] Содержит [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) структуры, если `dwKind` — `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [C++] Содержит [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) структуры, если `dwKind` — `TYPE_KIND_BUILT`.  
  
 Type.unused  
 Неиспользуемые заполнение.  
  
 type  
 Имя объединения.  
  
 unionmember  
 [Только в C#] Маршалинг это соответствующие структурный тип на основе `dwKind`.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) метод, где он заполняется. Интерпретация содержимое структуры на основе `dwKind` поля.  
  
> [!NOTE]
>  [C++] Если `dwKind` равняется `TYPE_KIND_BUILT`, то необходимо освободить базовый [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта при удалении `TYPE_INFO` структуры. Это выполняется с помощью вызова метода `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [Только в C#] В следующей таблице показаны интерпретации `unionmember` элемент для каждого типа. В примере показано, как это можно сделать для одного типа.  
  
|`dwKind`|`unionmember` интерпретируется как|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Пример  
 В этом примере показано, как интерпретировать `unionmember` членом `TYPE_INFO` структуры в C#. В этом примере показано Интерпретация только один тип (`TYPE_KIND_METADATA`), но остальные интерпретируются точно таким же образом.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)