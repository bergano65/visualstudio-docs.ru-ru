---
title: IDebugArrayObject::GetDimensions | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 781da7eadce78d5332befe91231131f02341574b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318996"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Возвращает размерность массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Параметры
`dwCount`\
[in] Число измерений для извлечения.

`dwDimensions`\
[in, out] Массив, который заполняется размеров каждого измерения. `dwCount` Указывает максимальный размер `dwDimensions` массива.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Многомерный массив может иметь разные размеры для каждого измерения. Например, если трехмерный массив `myarray[3][2][6]`, этот метод возвращает 3, 2 и 6 в `dwDimensions` параметр в указанном порядке.

## <a name="see-also"></a>См. также
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)