---
title: IDebugPortSupplier2::AddPort | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c674b73ad6ec45b1e388f62fbd3103afb5daedb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678233"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Добавляет порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

#### <a name="parameters"></a>Параметры
 `pRequest`

 [in] [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , описывающий порт, который будет добавляться.

 `ppPort`

 [out] Возвращает [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) объект, который представляет порт.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод фактически создает запрошенный порт, а также добавления поставщика порта внутренний список активных портов. [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) метод может вызываться сначала во избежание возможных простоев много времени.

## <a name="see-also"></a>См. также
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)