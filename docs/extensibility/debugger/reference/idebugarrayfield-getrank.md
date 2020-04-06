---
title: IDebugArrayField::GetRank Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736309"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Получает ранг или количество размеров массива.

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
(ваут) Возвращает ранг.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Ранг массива соответствует количеству размеров. В СЗ и СЗ многомерные массивы действительно представляют собой массивы массивов и поэтому их `GetRank` можно считать только одномерным массивом (и метод всегда возвращает 1). В [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], с другой стороны, многомерные массивы обрабатываются по-разному и ранг такого `GetRank` массива отражает количество измерений (и метод всегда возвращает количество измерений).

## <a name="see-also"></a>См. также
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
