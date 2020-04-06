---
title: IDebugArrayObject::GetCount Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736207"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Получает количество элементов в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Параметры
`pdwElements`\
(ваут) Возвращает счет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод рассматривает все элементы объекта массива как одномерный массив, даже если объект массива многомерный. Например, с `myarray[3][2][6]`учетом массива этот метод `pdwElements` возвращает 36 в параметре. Используйте метод [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) для извлечения отдельных элементов по одному.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
