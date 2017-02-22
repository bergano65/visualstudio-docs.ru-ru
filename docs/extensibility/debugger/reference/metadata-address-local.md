---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
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
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "Структура METADATA_ADDRESS_LOCAL"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Эта структура представляет адрес локальной переменной в пределах области \(как правило, функции или метода\).  
  
## Синтаксис  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## Термины  
 tokMethod  
 Идентификатор метода или функции локальной переменной.  
  
 \[C\+\+\] `_mdToken` a  `typedef` для обновления 32 \(sp2\)  `int`.  
  
 pLocal  
 Токен адрес которого данная структура представляет.  
  
 dwIndex  
 Могут быть индекс данной локальной переменной в методе или функции или другое значение \(языковой\).  
  
## Заметки  
 Эта структура является частью соединения в [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) когда структура  `dwKind` поле   `DEBUG_ADDRESS_UNION` структура имеет значение  `ADDRESS_KIND_LOCAL` \(значение  [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) перечисление\).  
  
 `Warning:` Только если \[C\+\+\]  `pLocal` не равны null, необходимо вызвать  `Release` указателя токена \(`addr` поле  [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура\):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)