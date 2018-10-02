---
title: METADATA_ADDRESS_LOCAL | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d59951fa73b4f5f10ab26abaad65fc2beab54837
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571568"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [METADATA_ADDRESS_LOCAL](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/metadata-address-local).  
  
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

