---
title: IDebugEnumField::GetUnderlyingSymbol | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b6b90f388f93bc7cfc2c246c529217bcdb00fa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920274"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Этот метод возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , представляющее имя перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Параметры
 `ppField`

 [out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) описывающий имя этого перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Имя перечисления также содержит тип перечисления, который привязан к ячейке памяти с помощью [привязать](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>См. также
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)