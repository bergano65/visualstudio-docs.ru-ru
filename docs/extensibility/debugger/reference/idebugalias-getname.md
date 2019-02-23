---
title: IDebugAlias::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5858c5b559720486c24bf3fbc7562a13b9fb8372
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683887"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
Возвращает имя псевдонима.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetName(
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

#### <a name="parameters"></a>Параметры
 `pbstrName`

 [out] Имя псевдонима.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)