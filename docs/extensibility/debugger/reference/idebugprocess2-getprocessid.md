---
title: IDebugProcess2::GetProcessId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b927d5a8da316faa76b5d102ad0cfb14e0cb61e7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706656"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Получает GUID для этого процесса.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

#### <a name="parameters"></a>Параметры
 `pguidProcessId`

 [out] Возвращает идентификатор GUID для этого процесса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Глобальный уникальный идентификатор (GUID) идентифицирует этот процесс от всех других процессов, запущенных в системе.

## <a name="see-also"></a>См. также
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)