---
title: IDebugProcess2::Detach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba166f67ad47da1e219ff767517e9b0664fe12aa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713442"
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