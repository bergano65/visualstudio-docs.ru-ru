---
title: "Структура DebugPropertyInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="debugpropertyinfo-structure"></a>Структура DebugPropertyInfo
Описывает объект иерархический характер, который имеет имя, тип и значение. Используется для описания свойств отладки локальных переменных, параметров, Контрольные значения переменных и выражений и регистрирует.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Члены  
 dwValidFields  
 Перечисляемого типа данных используется, чтобы указать, какие поля инициализируются.  
  
 bstrName  
 Имя свойства в контексте.  
  
 bstrType  
 Тип свойства как форматируемой строки.  
  
 bstrValue  
 Значение свойства как форматируемой строки.  
  
 bstrFullName  
 Полное имя свойства.  
  
 dwAttrib  
 Перечисление, указывающее флаги для атрибутов свойства отладки.  
  
 pDebugProp  
 `IDebugProperty` Описываемого сведения в этом `DebugPropertyInfo` структуры.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)