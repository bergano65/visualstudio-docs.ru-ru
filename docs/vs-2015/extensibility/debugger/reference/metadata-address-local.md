---
title: METADATA_ADDRESS_LOCAL | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5928f6092adc62dc8f0eb075f20367c056fc50c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547173"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 `Warning:` [C++ только]  Если `pLocal` не равно null, то нужно вызвать `Release` маркеров указателя (`addr` — это поле в [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры):  
  
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
