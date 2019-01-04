---
title: CONSTRUCTOR_ENUM | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 199201037889dbcb1b3019ef7632fc81e9c88db4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958661"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Выбирает различные типы конструкторов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Участники  
 crAll  
 Выбирает все конструкторы.  
  
 crNonStatic  
 Выбирает конструкторы не статическими.  
  
 crStatic  
 Выбирает статические конструкторы.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)