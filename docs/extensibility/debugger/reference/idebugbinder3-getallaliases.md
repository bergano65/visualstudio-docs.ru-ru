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
ms.openlocfilehash: ed8545431dc0cb643ba18d415285447f8a66f66e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923709"
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

#### <a name="parameters"></a>Параметры
 `uRequest`

 [in] Максимальное количество псевдонимов для возврата (указывает длину массива, передаваемого в `ppAliases`).

 `ppAliases`

 [in, out] Массив байтов с помощью псевдонима (если это значение null и `uRequest` равно 0, будет возвращаться количество псевдонимов, которые могут быть возвращены `puFetched`).

 `puFetched`

 [out] Возвращает количество получить псевдонимы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)