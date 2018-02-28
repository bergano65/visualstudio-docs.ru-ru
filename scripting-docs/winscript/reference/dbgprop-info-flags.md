---
title: "DBGPROP_INFO_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9821cde6c159712ff44438b74eea0f8e01247155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
Используется для указания `DebugPropertyInfo` поля  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 Инициализирует `bstrName` поля.  
  
 DBGPROP_INFO_TYPE  
 Инициализирует `bstrType` поля.  
  
 DBGPROP_INFO_VALUE  
 Инициализирует `bstrValue` поля.  
  
 DBGPROP_INFO_FULLNAME  
 Инициализирует `bstrFullName` поля.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Инициализирует `dwAttrib` поля.  
  
 DBGPROP_INFO_DEBUGPROP  
 Инициализирует `pDebugProp` поле, содержащее `IDebugProperty` интерфейса.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Указывает, поле значений должен содержать значение развернут автоматически, если он доступен для этого типа объектов.  
  
## <a name="see-also"></a>См. также  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)