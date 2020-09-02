---
title: 'Идебугфиелд:: Equals | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8a45a31c02376f95c3cd6b0c4a4adf0434fabe92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729010"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Этот метод сравнивает это поле с указанным полем для проверки на равенство.

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
окне Поле для сравнения с данным полем.

## <a name="return-value"></a>Возвращаемое значение
 Если поля совпадают, возвращает `S_OK` . Если поля отличаются, `S_FALSE.` в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
