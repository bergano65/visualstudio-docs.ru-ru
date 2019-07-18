---
title: IDebugReference2::GetDerivedMostReference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8775087b9ec212f7e7d7e1547d01a5f175c4dc22
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329829"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Получает ссылку на производный ссылку. Зарезервировано для будущего использования.

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
[out] Возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , представляющий свойство производного.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="remarks"></a>Примечания
 Например, если это свойство описывает объект, реализующий `ClassRoot` , но это фактически является экземпляром `ClassDerived` , производный от `ClassRoot`, этот метод возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объекта Представляет ссылку на `ClassDerived` объекта.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)