---
title: "Перечисление DOCUMENTNAMETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE — перечисление"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Перечисление DOCUMENTNAMETYPE
Описывает, печатаемых для получения для документа.  
  
## Синтаксис  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## Члены  
  
|Элемент|Описание|  
|-------------|--------------|  
|DOCUMENTNAMETYPE\_APPNODE|Возвращает имя, отображаемое в дерево приложения.|  
|DOCUMENTNAMETYPE\_TITLE|Возвращает имя, отображаемое в заголовке окна просмотра.|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|Получает имя файла без пути.|  
|DOCUMENTNAMETYPE\_URL|Получает URL\-адрес документа.|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|Возвращает заголовок, добавленный с перечислением для идентификации.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)