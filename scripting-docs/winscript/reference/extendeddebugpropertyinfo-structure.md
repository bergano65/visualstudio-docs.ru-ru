---
title: Структура ExtendedDebugPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62b9f3b5877f7919a57e9747355276e438240796
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888909"
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
  
## <a name="members"></a>Участники  
 `dwValidFields`  
 Тип перечислимых данных, можно указать, какие поля инициализируются.  
  
 `bstrName`  
 Имя свойства в контексте.  
  
 `bstrType`  
 Тип свойства как форматируемой строки.  
  
 `bstrValue`  
 Значение свойства как отформатированную строку.  
  
 `bstrFullName`  
 Полное имя свойства.  
  
 `dwAttrib`  
 Перечисление, содержащее флаги для атрибутов свойства отладки.  
  
 `pDebugProp`  
 `IDebugProperty` Объект, соответствующий данному `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Идентификатор диспетчера.  
  
 `nType`  
 Тип расширенного свойства.  
  
 `varValue`  
 Значение расширенного свойства, если он помещается в тип VARIANT.  
  
 `plbValue`  
 Байты фактических данных значения свойства.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` Объект, соответствующий данному `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>См. также  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Интерфейс IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)