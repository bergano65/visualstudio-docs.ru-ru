---
title: DBGPROP_ATTRIB_FLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_ATTRIB_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3170e310aa3177e2ca7a1dd81ead02bcc4050114
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572593"
---
# <a name="dbgprop_attrib_flags"></a>DBGPROP_ATTRIB_FLAGS
Описывает различные атрибуты для `IDebugProperty`. Член структуры `DebugPropertyInfo`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Члены  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Указывает, что атрибуты отсутствуют.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Указывает, что значение в `DebugPropertyInfo::bstrValue` является недопустимым.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Указывает, что ссылка или свойство имеет дочерние элементы.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Указывает, что значение доступно только для чтения.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Указывает объект, имеющий общий доступ.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Указывает объект, имеющий закрытый доступ.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Указывает объект, имеющий защищенный доступ.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Указывает объект, имеющий финальный доступ.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Указывает глобальное хранилище.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Указывает статическое хранилище.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Указывает объект, который является свойством.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Указывает виртуальное хранилище.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Указывает, что тип объекта является константой.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Указывает, что этот слот синхронизируется по потокам.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Указывает, что этот слот является неустойчивым относительно постоянного хранилища.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Указывает, что этот слот имеет атрибуты, помимо этих стандартных битов.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Указывает, что значение является значением, возвращаемым из функции.  
  
## <a name="remarks"></a>Заметки  
 Эти флаги также используются для фильтрации дочерних элементов объекта. Значения могут объединяться с помощью побитового оператора ИЛИ.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)