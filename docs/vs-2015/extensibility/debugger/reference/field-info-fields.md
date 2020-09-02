---
title: FIELD_INFO_FIELDS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e3f947db7606d6f7495cb1d88591aafa9e9933b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423716"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, какие сведения следует получить о объекте [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Инициализируйте или используйте `bstrFullName` поле в структуре [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
 FIF_NAME  
 Инициализируйте или используйте `bstrName` поле в `FIELD_INFO` структуре.  
  
 FIF_TYPE  
 Инициализируйте или используйте `bstrType` поле в `FIELD_INFO` структуре.  
  
 FIF_MODIFIERS  
 Инициализируйте или используйте `bstrModifiers` поле в `FIELD_INFO` структуре.  
  
## <a name="remarks"></a>Remarks  
 Эти значения также передаются в качестве аргумента в метод " [info](../../../extensibility/debugger/reference/idebugfield-getinfo.md) ", чтобы указать, какие поля структуры [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) должны быть инициализированы.  
  
 Эти значения также используются в `dwFields` члене `FIELD_INFO` структуры для указания того, какие поля используются и являются допустимыми.  
  
 Эти флаги можно сочетать с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
