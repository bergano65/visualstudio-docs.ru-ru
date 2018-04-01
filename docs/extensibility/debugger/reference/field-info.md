---
title: FIELD_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 701d9a3419a2f88f3873ea2120251fabb25c1fa8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="fieldinfo"></a>FIELD_INFO
Эта структура описывает локальную переменную, параметр или другому полю.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Участники  
 dwFields  
 Сочетание флагов из [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) перечисления, которое указывает, какие элементы будут заполнены.  
  
 bstrFullName  
 Полное имя поля.  
  
 bstrName  
 Краткое имя поля.  
  
 bstrType  
 Тип поля.  
  
 dwModifiers  
 Сочетание флагов из [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) перечисление, описывающее поля.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) метод, где он заполняется.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)