---
title: "Перечисление JS_PROPERTY_ATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Перечисление JS_PROPERTY_ATTRIBUTES
Указывает атрибуты свойства.  
  
## Синтаксис  
  
```  
enum JS_PROPERTY_ATTRIBUTES  
{  
   JS_PROPERTY_ATTRIBUTE_NONE = 0,  
   JS_PROPERTY_HAS_CHILDREN = 0x1,  
   JS_PROPERTY_FAKE = 0x2,  
   JS_PROPERTY_METHOD = 0x4,  
   JS_PROPERTY_READONLY = 0x8,  
   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10  
} JS_PROPERTY_ATTRIBUTES;  
```  
  
## Члены  
  
|Имя|Описание|  
|---------|--------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Свойство не имеет атрибутов.|  
|`JS_PROPERTY_HAS_CHILDREN`|Свойство имеет дочерние элементы.|  
|`JS_PROPERTY_FAKE`|Свойство представляет фиктивный узел, например методы «\[\]».|  
|`JS_PROPERTY_METHOD`|Свойство метода.|  
|`JS_PROPERTY_READONLY`|Свойство доступно только для чтения.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Свойство WinRT указатель на собственный объект.|  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)