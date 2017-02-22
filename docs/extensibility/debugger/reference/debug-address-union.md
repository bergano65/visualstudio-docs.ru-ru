---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
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
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "Объединение DEBUG_ADDRESS_UNION"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает различные типы адресов.  
  
## Синтаксис  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## Термины  
 dwKind  
 Значение [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисление, определяющее способ интерпретации соединение.  
  
 addr.addrNative  
 \[C\+\+ содержит только\] [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) если структура  `dwKind` \= ADDRESS\_KIND\_NATIVE.  
  
 addr.addrThisRel  
 \[C\+\+ содержит только\][UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) если структура  `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE.  
  
 addr.addUPhysical  
 \[C\+\+ содержит только\][UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) если структура  `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL.  
  
 addr.addrMethod  
 \[C\+\+ содержит только\][METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) если структура  `dwKind` \= ADDRESS\_KIND\_METHOD.  
  
 addr.addrField  
 \[C\+\+ содержит только\][METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) если структура  `dwKind` \= ADDRESS\_KIND\_FIELD.  
  
 addr.addrLocal  
 \[C\+\+ содержит только\][METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) если структура  `dwKind` \= ADDRESS\_KIND\_LOCAL.  
  
 addr.addrParam  
 \[C\+\+ содержит только\][METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) если структура  `dwKind` \= ADDRESS\_KIND\_PARAM.  
  
 addr.addrArrayElem  
 \[C\+\+ содержит только\][METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) если структура  `dwKind` \= ADDRESS\_KIND\_ARRAYELEM.  
  
 addr.addrRetVal  
 \[C\+\+ содержит только\][METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) если структура  `dwKind` \= ADDRESS\_KIND\_RETVAL.  
  
 addr.unused  
 \[C\+\+\] только заполнение.  
  
 addr  
 \[C\+\+\] только имя соединения.  
  
 unionmember  
 \[C\#\] только это значение нужно будет маршалировать по соответствующему типу структуры в соответствии on `dwKind`.  См. примечания для ассоциации  `dwKind` и интерпретация соединения.  
  
## Заметки  
 Эта структура является частью [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура и представляет один из нескольких разных типов адресов \(  `DEBUG_ADDRESS` структура заполняемую вызовом  [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) метод\).  
  
 \[C\#\] только в следующей таблице показано, как интерпретировать `unionmember` элемент для каждого типа адреса.  Пример показывает, как это делается для одного типа адреса.  
  
|`dwKind`|`unionmember` интерпретируется как|  
|--------------|----------------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## Пример  
 В этом примере показано, как интерпретировать один тип адреса \(`METADATA_ADDRESS_ARRAYELEM`\)   `DEBUG_ADDRESS_UNION` структура в c\#.  Остальные элементы можно интерпретировать способом те же.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)