---
title: DBGPROP_INFO_FLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572590"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Используется для указания `DebugPropertyInfo` полей  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Члены  
 DBGPROP_INFO_NAME  
 Инициализирует поле `bstrName`.  
  
 DBGPROP_INFO_TYPE  
 Инициализирует поле `bstrType`.  
  
 DBGPROP_INFO_VALUE  
 Инициализирует поле `bstrValue`.  
  
 DBGPROP_INFO_FULLNAME  
 Инициализирует поле `bstrFullName`.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Инициализирует поле `dwAttrib`.  
  
 DBGPROP_INFO_DEBUGPROP  
 Инициализирует `pDebugProp` поле, содержащее интерфейс `IDebugProperty`.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Указывает, что поле значения должно содержать автоматическое развернутое значение (если доступно) для этого типа объекта.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [структуры дебугпропертинфо](../../winscript/reference/debugpropertyinfo-structure.md)  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)