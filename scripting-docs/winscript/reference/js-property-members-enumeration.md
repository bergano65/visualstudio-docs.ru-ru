---
title: "Перечисление JS_PROPERTY_MEMBERS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_MEMBERS
apilocation: jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Перечисление JS_PROPERTY_MEMBERS
Флаги для задания типа информации, возвращаемой в запросе для членов объекта.  
  
## Синтаксис  
  
```  
enum JS_PROPERTY_MEMBERS  
{  
   JS_PROPERTY_MEMBERS_ALL = 0,  
   JS_PROPERTY_MEMBERS_ARGUMENTS = 1  
} JS_PROPERTY_MEMBERS;  
```  
  
## Члены  
  
### Значения  
  
|Имя|Описание|  
|---------|--------------|  
|`JS_PROPERTY_MEMBERS_ALL`|Представляет запрос список всех членов.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|Представляет запрос перечисления только аргументы.|  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)