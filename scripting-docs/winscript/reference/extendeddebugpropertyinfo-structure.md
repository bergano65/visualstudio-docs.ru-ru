---
title: Структура Екстендеддебугпропертинфо | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575838"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Структура ExtendedDebugPropertyInfo
Расширяет структуру `DebugPropertyInfo` с помощью дополнительных элементов, характеризующих расширенное свойство.  
  
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
 Перечислимый тип данных, используемый для указания, какие поля инициализируются.  
  
 `bstrName`  
 Имя свойства в контексте.  
  
 `bstrType`  
 Тип свойства в виде форматированной строки.  
  
 `bstrValue`  
 Значение свойства в виде форматированной строки.  
  
 `bstrFullName`  
 Полное имя свойства.  
  
 `dwAttrib`  
 Перечисление, указывающее флаги для атрибутов свойств отладки.  
  
 `pDebugProp`  
 `IDebugProperty` объект, соответствующий этому `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Идентификатор диспетчеризации.  
  
 `nType`  
 Тип расширенного свойства.  
  
 `varValue`  
 Значение расширенного свойства, если оно может уместиться в ВАРИАНТе.  
  
 `plbValue`  
 Фактические байты данных значения свойства.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` объект, соответствующий этому `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [структуры дебугпропертинфо](../../winscript/reference/debugpropertyinfo-structure.md)  
 @No__t_1 [интерфейса IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 [интерфейса идебужекстендедпроперти](../../winscript/reference/idebugextendedproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)