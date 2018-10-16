---
title: FIELD_MODIFIERS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0040795564aa1d1d599a55928b888ec7cfcfd97e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106780"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Задает модификаторы для типа поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Участники  
 FIELD_MOD_ACCESS_TYPE  
 Указывает, что поле не доступен.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Указывает, что поле имеет общий доступ.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Указывает, что поле имеет защищенный доступ.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Указывает, что поле имеет закрытый доступ.  
  
 FIELD_MOD_NOMODIFIERS  
 Указывает, что поле не содержит модификаторы.  
  
 FIELD_MOD_STATIC  
 Указывает, что поле является статическим.  
  
 FIELD_MOD_CONSTANT  
 Указывает, что поле является константой.  
  
 FIELD_MOD_TRANSIENT  
 Указывает, что поле является временным.  
  
 FIELD_MOD_VOLATILE  
 Указывает, что поле volatile.  
  
 FIELD_MOD_ABSTRACT  
 Указывает, что поле является абстрактным.  
  
 FIELD_MOD_NATIVE  
 Указывает, что поле является собственным.  
  
 FIELD_MOD_SYNCHRONIZED  
 Указывает, что это поле синхронизируется.  
  
 FIELD_MOD_VIRTUAL  
 Указывает, что поле является виртуальным.  
  
 FIELD_MOD_INTERFACE  
 Указывает, что поле является интерфейсом.  
  
 FIELD_MOD_FINAL  
 Указывает, что это поле является последней.  
  
 FIELD_MOD_SENTINEL  
 Указывает, что поле метки.  
  
 FIELD_MOD_INNERCLASS  
 Указывает, что поле внутреннего класса.  
  
 FIELD_TYPE_OPTIONAL  
 Указывает, что поле является необязательным.  
  
 FIELD_MOD_BYREF  
 Указывает, что это поле является ссылочным аргументом. Это специально для аргументов метода.  
  
 FIELD_MOD_HIDDEN  
 Указывает, что поле должно скрытые или в другом контексте; например [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] Статические локальные переменные.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Указывает, что поле представляет объект с `IUnknown` интерфейса.  
  
 FIELD_MOD_SPECIAL_NAME  
 Указывает, что поле имеет специальное имя, например, `.ctor` для конструктора ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] только).  
  
 FIELD_MOD_HIDEBYSIG  
 Указывает, что поле имеет `Overloads` ключевое слово, применяемый к нему ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] только).  
  
 FIELD_MOD_WRITEONLY  
 Указывает, что это поле доступно только для записи. Это значение не включается в `FIELD_MOD_ALL`, как только такие поля только для записи используется для вычисления функции. Пользователь должен явно запросить `FIELD_MOD_WRITEONLY` поля.  
  
 FIELD_MOD_ACCESS_MASK  
 Указывает маску для доступ к полю.  
  
 FIELD_MOD_MASK  
 Указывает маску для модификаторы поля.  
  
## <a name="remarks"></a>Примечания  
 Используется для `dwModifiers` членом [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) структуры.  
  
 Эти значения также передаются в [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) метод, чтобы фильтровать по определенным полям.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)