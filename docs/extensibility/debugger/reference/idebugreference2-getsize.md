---
title: IDebugReference2::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetSize
helpviewer_keywords:
- IDebugReference2::GetSize
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 681cede68a2d649cd9f072b6c10e8476a9625f6e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683432"
---
# <a name="idebugreference2getsize"></a>IDebugReference2::GetSize
Получает размер в байтах, значение ссылки. Зарезервировано для будущего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

#### <a name="parameters"></a>Параметры
 `pdwSize`

 [out] Возвращает размер в байтах, значение ссылки.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)