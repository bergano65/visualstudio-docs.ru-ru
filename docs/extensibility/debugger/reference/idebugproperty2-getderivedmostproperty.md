---
title: IDebugProperty2::GetDerivedMostProperty | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1227cb697dc78a8833e304d775fb4b1af85a2a69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916636"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Возвращает свойство производного свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

#### <a name="parameters"></a>Параметры
 `ppDerivedMost`

 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий свойство производного.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_GETDERIVEDMOST_NO_DERIVED_MOST` Если отсутствует свойство производного для извлечения.

## <a name="remarks"></a>Примечания
 Например, если это свойство описывает объект, реализующий `ClassRoot` , но это фактически является экземпляром `ClassDerived` , производный от `ClassRoot`, этот метод возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта описания `ClassDerived` объекта.

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)