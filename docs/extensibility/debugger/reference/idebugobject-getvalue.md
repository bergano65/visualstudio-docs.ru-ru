---
title: IDebugObject::GetValue Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 45d555cbea6bf8239ef4527ba982072e17532af4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726540"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Получает значение объекта в виде последовательной серии байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int GetValue(
   ref byte[] pValue,
   uint nSize
);
```

## <a name="parameters"></a>Параметры
`pValue`\
(в, вне) Массив, заполняемый последовательной серией байтов, представляющих ценность объекта.

`nSize`\
(в) Максимальное количество байтов для получения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Получите общее количество байтов значения, которые можно получить, позвонив в метод [GetSize.](../../../extensibility/debugger/reference/idebugobject-getsize.md)

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
