---
title: Перечисление SOURCE_TEXT_ATTR | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: dc5e7a7bb6c91bd852a8fd2024b708166c085209
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349781"
---
# <a name="sourcetextattr-enumeration"></a>Перечисление SOURCE_TEXT_ATTR
Описывают атрибуты отдельного символа исходного текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Участники  
  
|Член|Значение|Описание:|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Символ является частью ключевое слово языка, например, ключевое слово VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Символ является частью блок комментариев.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Символ не является частью скомпилированный язык исходного текста. Например HTML, окружающий блок сценария.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Символ является частью языковой оператор. Например:, арифметический оператор **+**.|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Символ является Числовая константа языка.  Например константа 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Символ является частью языка строковая константа. Например строка «Hello, World!».|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Символ указывает на начало блока функции|  
  
## <a name="remarks"></a>Примечания  
 Как правило `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, и `IActiveScriptDebug::GetScriptTextAttributes` методы возвращают один атрибут текста на один знак, если:  
  
-   GETATTRTYPE_DEPSCAN флаг установлен, в этом случае метод может вернуть флаги SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP  
  
-   GETATTRFLAG_THIS флаг установлен, в этом случае метод может вернуть флаг SOURCETEXT_ATTR_THIS  
  
-   GETATTRFLAG_HUMANTEXT флаг установлен, в этом случае метод может вернуть флаг SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)