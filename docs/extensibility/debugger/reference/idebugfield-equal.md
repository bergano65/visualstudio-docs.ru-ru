---
title: IDebugField::Equal | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8af316c9669b00ae8316888c6a7072d4737dd23d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352666"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Этот метод сравнивает это поле с указанным полем на предмет равенства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Параметры
`pField`\
[in] Поле для сравнения с этим параметром.

## <a name="return-value"></a>Возвращаемое значение
 Если поля не изменилось, возвращает `S_OK`. Если поля не совпадают, возвращает `S_FALSE.` в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)