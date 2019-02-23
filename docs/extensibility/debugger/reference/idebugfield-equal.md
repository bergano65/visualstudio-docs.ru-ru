---
title: IDebugField::Equal | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed978355aa752730cfb43390b3e4b6f80d327f83
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693949"
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

#### <a name="parameters"></a>Параметры
 `pField`

 [in] Поле для сравнения с этим параметром.

## <a name="return-value"></a>Возвращаемое значение
 Если поля не изменилось, возвращает `S_OK`. Если поля не совпадают, возвращает `S_FALSE.` в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)