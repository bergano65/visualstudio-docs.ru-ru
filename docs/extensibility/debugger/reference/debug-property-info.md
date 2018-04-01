---
title: DEBUG_PROPERTY_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 04ac40eea5223122a4da5187419ce5b5ed3c1bd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
Содержит сведения о свойстве отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>Участники  
 dwValidFields  
 Сочетание флагов из [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) перечисления, которое указывает, какие поля заполнены.  
  
 bstrFullName  
 Полное имя свойства.  
  
 bstrName  
 Имя свойства в контексте.  
  
 bstrType  
 Тип свойства как отформатированную строку.  
  
 bstrValue  
 Значение свойства как отформатированную строку.  
  
 pProperty  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта, описанного этой структурой.  
  
 dwAttrib  
 Сочетание флагов из [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) перечисление, описывающее атрибуты данного свойства.  
  
## <a name="remarks"></a>Примечания  
 Свойство является объектом иерархический характер, который имеет имя, тип и значение. Например свойство можно описать локальных переменных, параметров, Контрольные значения переменных и выражений и регистры.  
  
 Эта структура передается [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод, где он заполняется. Эта структура также возвращается как часть списка из этой структуры [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) интерфейс, который в свою очередь, возвращается из вызова [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) и [ EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) методы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)