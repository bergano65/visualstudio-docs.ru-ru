---
title: 'Иенумдебугкустоматтрибутес:: Clone | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Clone
helpviewer_keywords:
- IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1680c2e68a72c985236e501281100fa4e8b7d1f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929385"
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Clone ( 
   IEnumCustomAttributes** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
[out] Возвращает копию этого перечисления как отдельный объект.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Копия перечисления имеет то же состояние, что и оригинал, во время вызова этого метода. Однако исходное состояние копии и исходного состояния является отдельным и может быть изменено по отдельности.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
