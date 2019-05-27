---
title: IDebugStackFrame2::EnumProperties | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 427e76036329eef95398787a87d795538c480ba7
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66208718"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Создает перечислитель для свойства, связанные с этим кадром стека, такие как локальные переменные.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Параметры
`dwFieldSpec`\
[in] Сочетание флагов из [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, указывающее, какие поля в перечисленных [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры должны быть заполнены.

`nRadix`\
[in] Основание системы счисления для использования в любой числовой сведения о форматировании.

`refiid`\
[in] Идентификатор GUID фильтра, используемого для выбора [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры являются перечисляемые, такие как `guidFilterLocals`.

`dwTimeout`\
[in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.

`pcelt`\
[out] Возвращает количество свойств в перечисление. Это то же самое, что и вызов метода [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) метод.

`ppEnum`\
[out] Возвращает [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий список требуемых свойств.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Так как этот метод позволяет все выбранные свойства требуется получить с помощью одного вызова, он выполняется быстрее, чем последовательно вызова [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) и [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) методы.

## <a name="see-also"></a>См. также
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)