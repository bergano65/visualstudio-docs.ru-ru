---
title: IDebugObject::IsReadOnly | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21c8a21f3cc85247f1cef4131768984f99fff764
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349962"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Определяет, является ли этот объект только для чтения.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Параметры
`pfIsReadOnly`\
[out] Возвращает ненулевое значение (`TRUE`) Если этот объект является только для чтения; в противном случае, возвращает 0 (`FALSE`).

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Объект только для чтения, не может иметь значение, изменяющееся после его создания.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)