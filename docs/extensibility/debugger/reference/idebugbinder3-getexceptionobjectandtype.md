---
title: 'IDebugBinder3:: Жетексцептионобжектандтипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee86b12b16cc76b8e2c06ede5ec0110322b515ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891232"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Этот метод извлекает исключение, связанное с объектом, если таковой имеется.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Параметры
`ppException`\
заполняет Возвращает объект, представляющий исключение.

`ppField`\
заполняет Возвращает объект, представляющий конкретное поле, которое может вызвать исключение (это может быть значение null).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

> [!NOTE]
> Чтобы проверить, существует ли исключение, проверьте значение, возвращаемое `ppException` : если это значение null, то исключение не связано с этим объектом.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
