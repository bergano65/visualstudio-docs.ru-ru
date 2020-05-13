---
title: IDebugBinder3::GetAllAliases Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735818"
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
(в) Максимальное количество псевдонимов для возврата (указывает длину массива, `ppAliases`передаваемого в).

`ppAliases`\
(в, вне) Массив для заполнения псевдонимами (если это нулевое значение и `uRequest` 0, количество псевдонимов, которые `puFetched`могут быть возвращены, будет возвращено).

`puFetched`\
(ваут) Возвращает количество полученных псевдонимов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
