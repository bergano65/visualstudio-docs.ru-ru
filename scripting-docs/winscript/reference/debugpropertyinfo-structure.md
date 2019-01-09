---
title: Структура DebugPropertyInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47c0f6a359341d19b99c1ce8c099ebf1c6d6a1ff
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088989"
---
# <a name="debugpropertyinfo-structure"></a>Структура DebugPropertyInfo
Описывает объект иерархическую сущность, которая имеет имя, тип и значение. Он используется для описания свойств отладки локальных переменных, параметров, Контрольные значения переменных и выражений и регистрирует.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 Тип перечислимых данных, можно указать, какие поля инициализируются.  
  
 bstrName  
 Имя свойства в контексте.  
  
 bstrType  
 Тип свойства как форматируемой строки.  
  
 bstrValue  
 Значение свойства, как форматируемой строки.  
  
 bstrFullName  
 Полное имя свойства.  
  
 dwAttrib  
 Перечисление, содержащее флаги для атрибутов свойства отладки.  
  
 pDebugProp  
 `IDebugProperty` Описываемого сведения в этом `DebugPropertyInfo` структуры.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)