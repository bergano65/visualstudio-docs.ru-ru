---
title: IDebugPortEx2::CanTerminateProcess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12f8ad884045939c13f56e6a527643837be94d09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871755"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Определяет, можно ли завершить процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanTerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
HRESULT CanTerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

#### <a name="parameters"></a>Параметры
 `pPortProcess`

 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, представляющий к завершению процесса.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает `S_OK` Если может быть завершен процесс; в противном случае возвращает `S_FALSE`.

## <a name="see-also"></a>См. также
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)