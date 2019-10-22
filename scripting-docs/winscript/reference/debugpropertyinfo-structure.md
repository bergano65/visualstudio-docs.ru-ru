---
title: Структура Дебугпропертинфо | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575071"
---
# <a name="debugpropertyinfo-structure"></a>Структура DebugPropertyInfo
Описывает объект иерархической природы с именем, типом и значением. Он используется для описания свойств отладки локальных переменных, параметров, контрольных переменных и выражений, а также регистров.  
  
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
 дввалидфиелдс  
 Перечислимый тип данных, используемый для указания, какие поля инициализируются.  
  
 bstrName  
 Имя свойства в контексте.  
  
 бстртипе  
 Тип свойства в виде форматированной строки.  
  
 бстрвалуе  
 Значение свойства в виде форматированной строки.  
  
 бстрфуллнаме  
 Полное имя свойства.  
  
 дваттриб  
 Перечисление, указывающее флаги для атрибутов свойств отладки.  
  
 пдебугпроп  
 @No__t_0, описываемые данными в этой структуре `DebugPropertyInfo`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)