---
title: IDebugObject2::IsUserData | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04c47390f15ff59658ba25f5c8f93918a15f47d6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700098"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Определяет, представляет ли объект данных пользователя.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

#### <a name="parameters"></a>Параметры
 `pfUser`

 [out] Возвращает ненулевое значение (`TRUE`), если объект представляет данные пользователя; ноль (`FALSE`) Если это не так.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Данные пользователя — это любой объект, который является частью модуля, обозначены как JustMyCode (настраивается пользователем параметр, отмечающий модуля, как пользовательский код и поэтому отображаются в трассировке стека).

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)