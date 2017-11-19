---
title: "Перечисление SOURCE_TEXT_ATTR | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>Перечисление SOURCE_TEXT_ATTR
Описывают атрибуты отдельного символа исходного текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Члены  
  
|Член|Значение|Описание|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Символ является частью ключевое слово языка, например, ключевое слово VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Символ является частью блок комментариев.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Символ не является частью скомпилированный язык исходного текста. Например HTML, вокруг блок сценария.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Символ является частью оператор языка. Например:, арифметический оператор  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Символ является частью Числовая константа языка.  Например константа 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Символ является частью языка строковая константа. Например строка «Hello World».|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Символ указывает на начало блока функции|  
  
## <a name="remarks"></a>Примечания  
 Как правило `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, и `IActiveScriptDebug::GetScriptTextAttributes` методы возвращают один атрибут текстовый символ, если:  
  
-   Флаг GETATTRTYPE_DEPSCAN установлен, в этом случае метод может вернуть флаги SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP  
  
-   Флаг GETATTRFLAG_THIS установлен, в этом случае метод может вернуть флаг SOURCETEXT_ATTR_THIS  
  
-   В этом случае метод может возвратить SOURCETEXT_ATTR_HUMANTEXT флаг имеет значение флага GETATTRFLAG_HUMANTEXT.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)