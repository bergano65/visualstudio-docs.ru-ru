---
title: IDebugArrayObject::GetDimensions | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60ee75454bf105f12b79d60e032549bcb84ab465
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615236"
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