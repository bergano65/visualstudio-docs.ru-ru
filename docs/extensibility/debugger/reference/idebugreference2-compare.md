---
title: IDebugReference2::Compare | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df878cc59a47a8d3cc7079f8b919f87d9bb60f43
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457491"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Сравнивает одну ссылку на другой. Зарезервировано для будущего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Параметры
 `dwCompare`\

 [in] Значение из [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) перечисление, указывающее операцию сравнения, например, равно, меньше или больше.

 `pReference`\

 [in] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, представляющий ссылку на который требуется сравнить с.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)