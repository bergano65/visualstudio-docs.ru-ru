---
title: IEnumDebugPortSuppliers2::Next | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2e887c6e00587c4101c73c9cc6b5bdd0a47789
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164711"
---
# <a name="ienumdebugportsuppliers2next"></a>IEnumDebugPortSuppliers2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает следующий набор элементов из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   IDebugPortSupplier2** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                  celt,  
   IDebugPortSupplier2[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество извлекаемых элементов. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [in, out] Массив [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) элементов для заполнения.  
  
 `pceltFetched`  
 [out] Возвращает количество элементов, фактически возвращенных в `rgelt`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше, чем запрошенное количество элементов может быть возвращено; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
