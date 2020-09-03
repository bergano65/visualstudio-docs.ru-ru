---
title: 'Идебугаррайобжект:: Rank | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c645683cf1f842afdecba3c3dee8942a3fd6971a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736187"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Возвращает ранг массива, то есть количество измерений.

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
заполняет Возвращает ранг.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Используйте метод [Dimension](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) , чтобы получить размер каждого измерения объекта массива.

## <a name="see-also"></a>См. также раздел
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
