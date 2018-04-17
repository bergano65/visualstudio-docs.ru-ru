---
title: METADATA_ADDRESS_LOCAL | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 720f150be1b7cf992f0949750dd52218939c7d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
Эта структура представляет собой адрес локальной переменной в области (обычно функция или метод).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Термины  
 tokMethod  
 Идентификатор метода или функции локальной переменной является частью.  
  
 [C++] `_mdToken` — `typedef` для 32-разрядных `int`.  
  
 pLocal  
 Токен, эта структура представляет адрес.  
  
 dwIndex  
 Может быть индекс данной локальной переменной в метод или функция или любое другое значение (зависящие от языка).  
  
## <a name="remarks"></a>Примечания  
 Эта структура является частью объединения в [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры при `dwKind` поле `DEBUG_ADDRESS_UNION` структуры задано значение `ADDRESS_KIND_LOCAL` (значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Перечисление).  
  
 `Warning:` [C++]  Если `pLocal` не равно null, то необходимо вызвать `Release` маркеров указателя (`addr` — это поле в [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)