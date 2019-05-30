---
title: IDebugArrayField::GetRank | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d5118ffa045ccc2315ccb596850be6922fc2ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321690"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Возвращает ранг или число измерений массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Параметры
`pdwRank`\
[out] Возвращает ранг.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Ранг массива соответствует число измерений. В C++ и C# многомерных массивов, массивы массивов на самом деле являются и таким образом можно считать одномерного массива (и `GetRank` метод всегда возвращает значение 1). В [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], с другой стороны, многомерные массивы обрабатываются по-разному и ранг такой массив отражает число измерений (и `GetRank` метод всегда возвращает число измерений).

## <a name="see-also"></a>См. также
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)