---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает список дочерних элементов свойства.  
  
## Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
#### Параметры  
 `dwFields`  
 \[in\] сочетание пометит из [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисление, определяющее, перечисленные в полях  [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры быть заполняемым.  
  
 `dwRadix`  
 \[in\] определяет корень, используемый в отформатировать любое числовое сведения.  
  
 `guidFilter`  
 \[in\] идентификатор GUID фильтра, используемого с `dwAttribFilter` и  `pszNameFilter` параметры, которые следует выбрать, какие  `DEBUG_PROPERTY_INFO` дочерние элементы необходимо перечислить.  Например, `guidFilterLocals` фильтры для локальных переменных.  
  
 `dwAttribFilter`  
 \[in\] сочетание пометит из [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисление, которое определяет, какой тип объектов для перечисления, например  `DBG_ATTRIB_METHOD` для всех методов, которые могут быть дочерними элементами данного свойства.  Используется в сочетании с `guidFilter` и  `pszNameFilter` параметры.  
  
 `pszNameFilter`  
 \[in\] имя фильтра, используемого с `guidFilter` и  `dwAttribFilter` параметры, которые следует выбрать, какие  `DEBUG_PROPERTY_INFO` дочерние элементы необходимо перечислить.  Например, установка этого параметра в MyX" фильтры "для всех дочерних элементов с именем "MyX".  
  
 `dwTimeout`  
 \[in\] задает максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте `INFINITE` ждать бесконечно.  
  
 `ppEnum`  
 \[out\] возвращает [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объект, содержащий список свойств дочерних элементов.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)