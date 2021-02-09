---
title: 'IDebugProperty2:: Жетдериведмостпроперти | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f91b00d2f448aea2f187e37813782ce568ad859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916044"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Возвращает производное свойство свойства.

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

## <a name="parameters"></a>Параметры
`ppDerivedMost`\
заполняет Возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , представляющий производное свойство.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает, `S_GETDERIVEDMOST_NO_DERIVED_MOST` если не существует производного свойства для извлечения.

## <a name="remarks"></a>Remarks
 Например, если это свойство описывает объект, реализующий, `ClassRoot` но который на самом деле является экземпляром, `ClassDerived` производным от `ClassRoot` , то этот метод возвращает объект [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , описывающий `ClassDerived` объект.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
