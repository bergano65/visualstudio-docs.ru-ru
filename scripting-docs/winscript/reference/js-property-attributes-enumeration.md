---
title: Перечисление JS_PROPERTY_ATTRIBUTES | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed034ef6fc134838058b75534f1b5c17c1ec2e3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733774"
---
# <a name="jspropertyattributes-enumeration"></a>Перечисление JS_PROPERTY_ATTRIBUTES
Задает атрибуты свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Члены  
  
|Имя|Описание|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Свойство не имеет атрибутов.|  
|`JS_PROPERTY_HAS_CHILDREN`|Свойство имеет дочерние элементы.|  
|`JS_PROPERTY_FAKE`|Свойство представляет фиктивный узел, например «[методы]».|  
|`JS_PROPERTY_METHOD`|Свойство — это метод.|  
|`JS_PROPERTY_READONLY`|Свойство доступно только для чтения.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Свойство является указатель на собственный объект WinRT.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)