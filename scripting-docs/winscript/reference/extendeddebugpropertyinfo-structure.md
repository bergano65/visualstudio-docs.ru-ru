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
ms.openlocfilehash: e0251d4b578a33a9eb5448c1ceb2b2607f82d43a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096776"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Структура ExtendedDebugPropertyInfo
Расширяет `DebugPropertyInfo` структуры с помощью дополнительных членов, характеризующее расширенного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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