---
title: METADATA_ADDRESS_LOCAL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b29c9ec3d424dfb88f4cbe14e6e8baea87737d8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916694"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
Эта структура представляет собой адрес локальной переменной в области (обычно функцию или метод).  
  
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
 Токен, адрес которого эта структура представляет.  
  
 dwIndex  
 Может быть индекс данной локальной переменной в методе или функции или любое другое значение (зависящие от языка).  
  
## <a name="remarks"></a>Примечания  
 Эта структура является частью объединения в [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуры, когда `dwKind` поле `DEBUG_ADDRESS_UNION` структура присваивается `ADDRESS_KIND_LOCAL` (значение из [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Перечисление).  
  
 `Warning:` [C++]  Если `pLocal` не равно null, то нужно вызвать `Release` маркеров указателя (`addr` — это поле в [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры):  
  
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
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)