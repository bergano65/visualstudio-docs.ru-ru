---
title: IDebugObject::SetValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ccfea65f7f24b3d48fc5ec5d68028c72b9b4eece
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692661"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Задает значение объекта из последовательных последовательность байтов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

#### <a name="parameters"></a>Параметры
 `pValue`

 [in] Массив байтов, представляющий новое значение.

 `nSize`

 [in] Размер значения в байтах.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Значения в массиве копируются в это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекта, заменив существующие значения. Размер нового значения может быть больше или меньше, чем существующее. Это `IDebugObject` не может быть пустой ссылкой.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)