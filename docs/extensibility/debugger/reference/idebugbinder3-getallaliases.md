---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f54ad96b3e6e1832e63e858609a0a1d6ecbcc93e
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614782"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Этот метод извлекает список псевдонимов из программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Параметры
`uRequest`\
[in] Максимальное количество псевдонимов для возврата (указывает длину массива, передаваемого в `ppAliases`).

`ppAliases`\
[in, out] Массив байтов с помощью псевдонима (если это значение null и `uRequest` равно 0, будет возвращаться количество псевдонимов, которые могут быть возвращены `puFetched`).

`puFetched`\
[out] Возвращает количество получить псевдонимы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)