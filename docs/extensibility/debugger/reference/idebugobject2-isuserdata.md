---
title: 'IDebugObject2:: о. UserData | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c53281ee144d3a1fa771fe4e77bba6bb418356e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953361"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Определяет, представляет ли объект пользовательские данные.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Параметры
`pfUser`\
заполняет Возвращает ненулевое значение ( `TRUE` ), если объект представляет пользовательские данные; ноль ( `FALSE` ), если это не так.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Пользовательские данные — это любой объект, который является частью модуля, обозначенного как Жустмикоде (настраиваемый пользователем параметр, который помечает модуль как пользовательский код и, следовательно, отображается в трассировке стека).

## <a name="see-also"></a>См. также раздел
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
