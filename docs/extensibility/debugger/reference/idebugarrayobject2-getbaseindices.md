---
title: IDebugArrayObject2::GetBaseIndices | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9b445f8ec471774eaceb0d6dd06c44b7d167f79
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615206"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Получает базовый индексы (нижней границы) для каждого индекса, учитывая количество измерений в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>Параметры
`dwRank`\
[in] Число измерений (рангом) массива.

`dwIndices`\
[out] Базовый индексы (нижней границы) для массива.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Например, эта функция должна вернуть "5" для массива, созданные ниже C# кода:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>См. также
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)