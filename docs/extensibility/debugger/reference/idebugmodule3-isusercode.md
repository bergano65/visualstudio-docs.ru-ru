---
title: IDebugModule3::IsUserCode | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39bbef1e8b831473b196d0609459b80a05e5fc2c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718499"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Извлекает сведения о представляет ли модуль пользовательским кодом или нет.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

#### <a name="parameters"></a>Параметры
 `pfUser`

 [out] Ненулевое значение (`TRUE`), если модуль представляет пользовательский код, ноль (`FALSE`) Если это не так.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)