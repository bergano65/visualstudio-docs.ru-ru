---
title: Перечисление SOURCE_TEXT_ATTR | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573003"
---
# <a name="source_text_attr-enumeration"></a>Перечисление SOURCE_TEXT_ATTR
Описывают атрибуты отдельного символа исходного текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Члены  
  
|Член|значения|Описание|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Символ является частью ключевого слова языка, например ключевое слово VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Символ является частью блока комментариев.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Символ не является частью текста исходного кода на скомпилированном языке. Например, HTML-код, окружающий Блок script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Символ является частью оператора языка. Например: арифметический оператор **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Символ является частью числовой константы языка.  Например, константа 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Символ является частью строковой константы языка. Например, строка "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Символ указывает на начало блока функции|  
  
## <a name="remarks"></a>Заметки  
 Как правило, методы `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` и `IActiveScriptDebug::GetScriptTextAttributes` возвращают один текстовый атрибут на символ, если только не:  
  
- Установлен флаг GETATTRTYPE_DEPSCAN, в этом случае метод может возвращать флаги SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
- Установлен флаг GETATTRFLAG_THIS, в этом случае метод может вернуть флаг SOURCETEXT_ATTR_THIS,  
  
- Установлен флаг GETATTRFLAG_HUMANTEXT, в этом случае метод может вернуть флаг SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)