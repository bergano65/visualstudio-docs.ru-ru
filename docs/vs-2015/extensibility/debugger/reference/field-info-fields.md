---
title: FIELD_INFO_FIELDS | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c181d1483dc33e8931436c24fc3cf681d182ab34
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570311"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [FIELD_INFO_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/field-info-fields).  
  
Указывает, какую информацию нужно извлечь о [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

