---
title: IDebugProperty2::EnumChildren | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cfbce26a84254158f088e8744c14154aef7f61a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681391"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Получает список дочерних элементов свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

#### <a name="parameters"></a>Параметры
 `dwFields`

 [in] Сочетание флагов из [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, указывающее, какие поля в перечисленных [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры должны быть заполнены.

 `dwRadix`

 [in] Задает основание системы счисления для использования в любой числовой сведения о форматировании.

 `guidFilter`

 [in] Идентификатор GUID фильтр, используемый с `dwAttribFilter` и `pszNameFilter` параметров для выбора, который `DEBUG_PROPERTY_INFO` дочерние элементы, которые необходимо перечислить. Например `guidFilterLocals` фильтры для локальных переменных.

 `dwAttribFilter`

 [in] Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисления, указывающее, какие типы объектов для перечисления, например `DBG_ATTRIB_METHOD` для всех методов, которые могут быть дочерние элементы этого свойства. Используется в сочетании с `guidFilter` и `pszNameFilter` параметров.

 `pszNameFilter`

 [in] Имя фильтра, используемый с `guidFilter` и `dwAttribFilter` параметров для выбора, который `DEBUG_PROPERTY_INFO` дочерние элементы, которые необходимо перечислить. Например Установка этого параметра на «MyX» фильтры для всех дочерних элементов с именем «MyX.»

 `dwTimeout`

 [in] Указывает максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.

 `ppEnum`

 [out] Возвращает [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий список дочерних свойств.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)