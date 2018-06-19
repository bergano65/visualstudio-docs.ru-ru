---
title: IDebugProperty2::EnumChildren | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9631ee89dc9d241932b745db4ce094799a899bad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122214"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Возвращает список дочерних элементов свойства.  
  
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
 [in] Сочетание флагов из [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, указывающее, какие поля в перечислимого [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры должны быть заполнены.  
  
 `dwRadix`  
 [in] Определяет основание системы счисления, используемое в любой числовой сведения о форматировании.  
  
 `guidFilter`  
 [in] Идентификатор GUID фильтра, используемого с `dwAttribFilter` и `pszNameFilter` параметры, чтобы выбрать, какие `DEBUG_PROPERTY_INFO` дочерние элементы, подлежащие перечислению. Например `guidFilterLocals` фильтры для локальных переменных.  
  
 `dwAttribFilter`  
 [in] Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисления, которое указывает, какой тип объектов для перечисления, например `DBG_ATTRIB_METHOD` для всех методов, которые могут быть дочерние элементы данного свойства. Используется в сочетании с `guidFilter` и `pszNameFilter` параметров.  
  
 `pszNameFilter`  
 [in] Имя фильтра, используемого с `guidFilter` и `dwAttribFilter` параметры, чтобы выбрать, какие `DEBUG_PROPERTY_INFO` дочерние элементы, подлежащие перечислению. Например значение этого свойства равно «MyX» фильтры для всех дочерних элементов с именем «MyX.»  
  
 `dwTimeout`  
 [in] Указывает максимальное время (в миллисекундах) ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.  
  
 `ppEnum`  
 [out] Возвращает [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий список дочерних свойств.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)