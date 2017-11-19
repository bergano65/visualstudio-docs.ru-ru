---
title: "DEBUGPROP_INFO_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUGPROP_INFO_FLAGS
helpviewer_keywords: DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24b0208cdfd49ef07ba85803d03a1e2c4aa91553
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Указывает, какую информацию, чтобы получить сведения об объекте debug свойство.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Члены  
 DEBUGPROP_INFO_FULLNAME  
 Инициализация или использовать `bstrFullName` поле.  
  
 DEBUGPROP_INFO_NAME  
 Инициализация или использовать `bstrName` поле.  
  
 DEBUGPROP_INFO_TYPE  
 Инициализация или использовать `bstrType` поле.  
  
 DEBUGPROP_INFO_VALUE  
 Инициализация или использовать `bstrValue` поле.  
  
 DEBUGPROP_INFO_ATTRIB  
 Инициализация или использовать `dwAttrib` поле.  
  
 DEBUGPROP_INFO_PROP,  
 Инициализация или использовать `pProperty` поле, содержащее [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейса.  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Указывает, поле значений должен содержать значение развернут автоматически, если он доступен для этого типа объектов.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Не рекомендуется.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Возвращает все значения beautified или члены (то есть не форматировать значения).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Не возвращают специальные синтезированную значения (например, не следует вызывать `ToString()` на объект для получения значения).  
  
 DEBUGPROP_INFO_NONE  
 Указывает, что флаги не установлены.  
  
 DEBUGPROP_INFO_STANDARD  
 Инициализация или использовать `dwAttrib`, `bstrName`, `bstrType`, и `bstrValue` поля.  
  
 DEBUGPROP_INFO_All  
 Указывает маску всех флагов.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются в [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), и [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) методах, чтобы указать, какие поля должны быть инициализированы [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.  
  
 Эти значения также используются для `dwFields` членом `DEBUG_PROPERTY_INFO` структуры для указания поля структуры, используемые и допустимым при возврате структуры.  
  
 Эти значения могут объединяться с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)