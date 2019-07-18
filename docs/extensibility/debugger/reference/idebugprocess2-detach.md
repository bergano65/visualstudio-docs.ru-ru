---
title: IDebugProcess2::Detach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3948ecce15b9b2b2e8b3bf974ecc2277d9fa0360
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353198"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Отсоединяет отладчика от этого процесса путем отсоединения всех программ в процессе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Все программы и процесс продолжать работать, но больше не являются частью сеанса отладки. После отсоединения операции завершения, не более отладки, которые будут отправляться события для этого процесса (и его программы).

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)