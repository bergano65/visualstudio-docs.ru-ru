---
title: "DBGPROP_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_ATTRIB_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_ATTRIB_FLAGS"
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DBGPROP_ATTRIB_FLAGS
Описывает различные атрибуты для `IDebugProperty`.  Член структуры `DebugPropertyInfo`.  
  
## Синтаксис  
  
```  
enum { DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,    DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,    DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,    DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,    DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,    DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,    DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,    DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,    DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,    DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,    DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,    DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,    DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,    DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,    DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,    DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000    DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000, };   
```  
  
## Члены  
 DBGPROP\_ATTRIB\_NO\_ATTRIB  
 Указывает, что атрибуты отсутствуют.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_INVALID  
 Указывает, что значение в `DebugPropertyInfo::bstrValue` является недопустимым.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_EXPANDABLE  
 Указывает, что ссылка или свойство имеет дочерние элементы.  
  
 DBGPROP\_ATTRIB\_VALUE\_READONLY  
 Указывает, что значение доступно только для чтения.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PUBLIC  
 Указывает объект, имеющий общий доступ.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PRIVATE  
 Указывает объект, имеющий закрытый доступ.  
  
 DBGPROP\_ATTRIB\_ACCESS\_PROTECTED  
 Указывает объект, имеющий защищенный доступ.  
  
 DBGPROP\_ATTRIB\_ACCESS\_FINAL  
 Указывает объект, имеющий финальный доступ.  
  
 DBGPROP\_ATTRIB\_STORAGE\_GLOBAL  
 Указывает глобальное хранилище.  
  
 DBGPROP\_ATTRIB\_STORAGE\_STATIC  
 Указывает статическое хранилище.  
  
 DBGPROP\_ATTRIB\_STORAGE\_FIELD  
 Указывает объект, который является свойством.  
  
 DBGPROP\_ATTRIB\_STORAGE\_VIRTUAL  
 Указывает виртуальное хранилище.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_CONSTANT  
 Указывает, что тип объекта является константой.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_SYNCHRONIZED  
 Указывает, что этот слот синхронизируется по потокам.  
  
 DBGPROP\_ATTRIB\_TYPE\_IS\_VOLATILE  
 Указывает, что этот слот является неустойчивым относительно постоянного хранилища.  
  
 DBGPROP\_ATTRIB\_HAS\_EXTENDED\_ATTRIBS  
 Указывает, что этот слот имеет атрибуты, помимо этих стандартных битов.  
  
 DBGPROP\_ATTRIB\_VALUE\_IS\_RETURN\_VALUE  
 Указывает, что значение является значением, возвращаемым из функции.  
  
## Заметки  
 Эти флаги также используются для фильтрации дочерних элементов объекта.  Значения могут объединяться с помощью побитового оператора ИЛИ.  
  
## См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)