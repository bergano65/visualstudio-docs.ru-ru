---
title: Перечисление JS_PROPERTY_ATTRIBUTES | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 27aaadfd1d3ff38e9a0382ff1863b73d2bccc325
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539447"
---
# <a name="jspropertyattributes-enumeration"></a>Перечисление JS_PROPERTY_ATTRIBUTES
Задает атрибуты свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Участники  
  
|name|Описание|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|Свойство не имеет атрибутов.|  
|`JS_PROPERTY_HAS_CHILDREN`|Свойство имеет дочерние элементы.|  
|`JS_PROPERTY_FAKE`|Свойство представляет поддельный узел, например «[методы]».|  
|`JS_PROPERTY_METHOD`|Свойство — это метод.|  
|`JS_PROPERTY_READONLY`|Свойство доступно только для чтения.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|Свойство является указатель на собственный объект WinRT.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)