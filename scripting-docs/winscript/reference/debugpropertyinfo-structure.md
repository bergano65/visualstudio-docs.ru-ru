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
ms.openlocfilehash: 0dca3dac5c2e55e512bd4f798ca4a9bce82f7e00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874193"
---
# <a name="debugpropertyinfo-structure"></a>Структура DebugPropertyInfo
Описывает объект иерархическую сущность, которая имеет имя, тип и значение. Он используется для описания свойств отладки локальных переменных, параметров, Контрольные значения переменных и выражений и регистрирует.  
  
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
  
## <a name="members"></a>Участники  
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