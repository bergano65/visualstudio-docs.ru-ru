---
title: FIELD_INFO_FIELDS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d74f39ce8e9e350c791371f20b7401d685fb1d18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Указывает, какую информацию для получения о [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_FIELD_INFO_FIELDS {   
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
 Инициализация или использовать `bstrFullName` в [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры.  
  
 FIF_NAME  
 Инициализация или использовать `bstrName` в `FIELD_INFO` структуры.  
  
 FIF_TYPE  
 Инициализация или использовать `bstrType` в `FIELD_INFO` структуры.  
  
 FIF_MODIFIERS  
 Инициализация или использовать `bstrModifiers` в `FIELD_INFO` структуры.  
  
## <a name="remarks"></a>Примечания  
 Эти значения также передана в качестве аргумента для [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) способа указать, какие поля [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры должны быть инициализированы.  
  
 Эти значения также используются в `dwFields` членом `FIELD_INFO` структуры указывает, какие поля используются и допустимым.  
  
 Эти флаги могут объединяться с битовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)