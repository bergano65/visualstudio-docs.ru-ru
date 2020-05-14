---
title: IDebugСправка2::GetDerivedMostСправка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15e98884d040cfb2ebf1b33a56c7edea331fbff0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720612"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Получает полученную наиболее ссылку на ссылку. Зарезервировано для последующего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Параметры
`ppDerivedMost`\
(ваут) Возвращает объект [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) представляющий наибольшее свойство, полученное из них.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="remarks"></a>Примечания
 Например, если это свойство описывает `ClassRoot` объект, который реализует, `ClassDerived` но который на `ClassRoot`самом деле является моменттивным, что происходит от `ClassDerived` , то этот метод возвращает [объект IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) представляющий ссылку на объект.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
