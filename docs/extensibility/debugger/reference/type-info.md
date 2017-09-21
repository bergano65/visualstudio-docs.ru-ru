---
title: "TYPE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TYPE_INFO"
helpviewer_keywords: 
  - "Структура TYPE_INFO"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта структура определяет различные типы сведения о представлении поля.  
  
## Синтаксис  
  
```cpp#  
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
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### Параметры  
 dwKind  
 Значение [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) перечисление, которое определяет, как интерпретировать соединение.  
  
 type.typeMeta  
 \[C\+\+\] содержит только a [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) если структура  `dwKind` существует  `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 \[C\+\+\] содержит только a [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) если структура  `dwKind` существует  `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 \[C\+\+\] содержит только a [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) если структура  `dwKind` существует  `TYPE_KIND_BUILT`.  
  
 type.unused  
 Неиспользуемая заполнение.  
  
 type  
 Имя соединения.  
  
 unionmember  
 \[C\#\] маршалируйте это только к соответствующему типу структуры в соответствии on `dwKind`.  
  
## Заметки  
 Эта структура передается [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) метод, в котором он заполнен.  Содержимое структуры, найденных на интерпретируются как `dwKind` поле.  
  
> [!NOTE]
>  Только если \[C\+\+\] `dwKind` equals  `TYPE_KIND_BUILT`после этого необходимо освободить помещения в основу  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объект уничтожение  `TYPE_INFO` структура.  Это делается путем вызова `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 \[C\#\] только в следующей таблице показано, как интерпретировать `unionmember` элемент для каждого типа.  Пример показывает, как это делается для одного типа.  
  
|`dwKind`|`unionmember` интерпретируется как|  
|--------------|----------------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## Пример  
 В этом примере показано, как интерпретировать `unionmember` элемент  `TYPE_INFO` структура в c\#.  Этот пример показывает интерпретировать только один тип \(`TYPE_KIND_METADATA`\), но другие интерпретировать способом те же.  
  
```c#  
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
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)