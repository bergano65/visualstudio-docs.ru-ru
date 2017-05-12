---
title: "Перечисление SOURCE_TEXT_ATTR | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR — константы"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Перечисление SOURCE_TEXT_ATTR
Опишите атрибуты одного символа исходного текста.  
  
## Синтаксис  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## Члены  
  
|Элемент|Значение|Описание|  
|-------------|--------------|--------------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|Символ является частью ключевого слова языка, например ключевого слова `While` VBScript.|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|Символ является частью " примечания ".|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|Символ не является частью компилированного исходного текста языка.  Например, HTML\) вокруг блока скрипта.|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|Символ части оператора языка.  Например: арифметический оператор, **\+**.|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|Знак числовой константы часть языка.  Например, константа 3,14159.|  
|SOURCETEXT\_ATTR\_STRING|0x0020|Символ является частью строковые константы языка.  Например, строка "hello world".|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|Символ, указывающий начало блока функции|  
  
## Заметки  
 Как правило, `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` и атрибут текста получения одного из методов `IActiveScriptDebug::GetScriptTextAttributes` в символ, если:  
  
-   Пометить GETATTRTYPE\_DEPSCAN устанавливается в этом случае метод может возвращать SOURCETEXT\_ATTR\_IDENTIFIER флаги, и SOURCETEXT\_ATTR\_MEMBERLOOKUP  
  
-   Пометить GETATTRFLAG\_THIS устанавливается в этом случае метод может вернуть пометить SOURCETEXT\_ATTR\_THIS,  
  
-   Пометить GETATTRFLAG\_HUMANTEXT устанавливается в этом случае метод может вернуть пометить SOURCETEXT\_ATTR\_HUMANTEXT.  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)