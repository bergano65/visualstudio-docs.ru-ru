---
title: FIELD_INFO_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 550490f677f2d63eabfeba61bcac2c49cb258217
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931423"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Указывает, какую информацию нужно извлечь о [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Участники  
 FIF_FULLNAME  
 Инициализация и использование `bstrFullName` в [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры.  
  
 FIF_NAME  
 Инициализация и использование `bstrName` в `FIELD_INFO` структуры.  
  
 FIF_TYPE  
 Инициализация и использование `bstrType` в `FIELD_INFO` структуры.  
  
 FIF_MODIFIERS  
 Инициализация и использование `bstrModifiers` в `FIELD_INFO` структуры.  
  
## <a name="remarks"></a>Примечания  
 Эти значения также передаются в качестве аргумента [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) метод, чтобы указать, какие поля из [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры должны быть инициализированы.  
  
 Эти значения также используются в `dwFields` членом `FIELD_INFO` структура указывает, какие поля используются и допустимым.  
  
 Эти флаги могут быть объединены с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)