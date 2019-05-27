---
title: IDebugCustomAttribute::GetParentField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6bdb5daee7fa0c2b8dc5228998a8ac0fd22fec0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205320"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Получает поле, к которому подключается настраиваемый атрибут.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Параметры
`ppField`\
[out] Возвращает [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , представляющий поле, к которому подключается настраиваемый атрибут.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызовите [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) метод возвращенного [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) является объектом, чтобы определить тип поля, которые родительского.

## <a name="see-also"></a>См. также
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)