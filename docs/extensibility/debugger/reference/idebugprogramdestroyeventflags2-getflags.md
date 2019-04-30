---
title: IDebugProgramDestroyEventFlags2::GetFlags | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugProgramDestroyEventFlags2::GetFlags
ms.assetid: dd53bd0c-459a-4077-ba81-780defb71e87
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b163da7d37983b41cb27d8db799817376784346
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870343"
---
# <a name="idebugprogramdestroyeventflags2getflags"></a>IDebugProgramDestroyEventFlags2::GetFlags
Извлекает программа уничтожить флаги.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetFlags(
   PROGRAM_DESTROY_FLAGS* pdwFlags
);
```

```csharp
public int GetFlags(
   out enum_PROGRAM_DESTROY_FLAGS pdwFlags
);
```

#### <a name="parameters"></a>Параметры
 `pdwFlags`

 [out] Представляет программу уничтожить флаги.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)
- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)