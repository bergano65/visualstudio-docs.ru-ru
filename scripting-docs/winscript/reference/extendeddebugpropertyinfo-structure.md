---
title: "Структура ExtendedDebugPropertyInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="extendeddebugpropertyinfo-structure"></a>Структура ExtendedDebugPropertyInfo
Расширяет `DebugPropertyInfo` структуры с помощью дополнительных членов, характеризующее расширенного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Члены  
 `dwValidFields`  
 Перечисляемого типа данных используется, чтобы указать, какие поля инициализируются.  
  
 `bstrName`  
 Имя свойства в контексте.  
  
 `bstrType`  
 Тип свойства как форматируемой строки.  
  
 `bstrValue`  
 Значение свойства как отформатированную строку.  
  
 `bstrFullName`  
 Полное имя свойства.  
  
 `dwAttrib`  
 Перечисление, указывающее флаги для атрибутов свойства отладки.  
  
 `pDebugProp`  
 `IDebugProperty`Объект, соответствующий этому `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Идентификатор диспетчеризации.  
  
 `nType`  
 Тип расширенного свойства.  
  
 `varValue`  
 Значение расширенного свойства, если он помещается в тип VARIANT.  
  
 `plbValue`  
 Байты данных фактические значения свойства.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`Объект, соответствующий этому `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>См. также  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Интерфейс IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)