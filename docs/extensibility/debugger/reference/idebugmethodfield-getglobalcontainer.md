---
title: IDebugMethodField::GetGlobalContainer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcd816b74e5c1474e89ab5b9550df8787c8210ee
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211957"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Возвращает контейнер глобального метода.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Параметры
`ppClass`\
[out] Возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) представляющий модуль, в котором определен этот метод.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Возвращенный [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект представляет весь модуль и является объектом искусственного, то есть сам модуль не имеют фактический класс, но она может быть представлена `IDebugClassField` объектам, различных элементы модуля перечисления и обнаружения.

## <a name="see-also"></a>См. также
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)