---
title: IDebugStackFrame2::EnumProperties | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0f32eac31b9b42a263ee57925f1fa8a785a1131
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Создает перечислитель для свойства, связанные с этим кадром стека, например локальные переменные.  
  
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
  
#### <a name="parameters"></a>Параметры  
 `dwFieldSpec`  
 [in] Сочетание флагов из [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, указывающее, какие поля в перечислимого [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры должны быть заполнены.  
  
 `nRadix`  
 [in] Основание системы счисления, используемое в любой числовой сведения о форматировании.  
  
 `refiid`  
 [in] Идентификатор GUID фильтра, используемого для выбора [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры, перечисления, таких как `guidFilterLocals`.  
  
 `dwTimeout`  
 [in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.  
  
 `pcelt`  
 [out] Возвращает количество свойств перечисления. Это то же самое, что и вызов метода [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) метод.  
  
 `ppEnum`  
 [out] Возвращает [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий список требуемых свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Так как этот метод позволяет получить с помощью одного вызова все выбранные свойства, они выполняются быстрее последовательного вызова [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) и [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) методы.  
  
## <a name="see-also"></a>См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)