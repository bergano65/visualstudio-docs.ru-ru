---
title: IDebugArrayField::GetNumberOfElements | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86cd2b227926db38c5bd50fa0457688a023bc7e3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704115"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Возвращает количество элементов в массиве.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

#### <a name="parameters"></a>Параметры
 `pdwNumElements`

 [out] Возвращает количество элементов в массиве.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Возвращаемое значение общее число элементов в массиве, независимо от количества измерений.

## <a name="see-also"></a>См. также
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)