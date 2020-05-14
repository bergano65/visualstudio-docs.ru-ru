---
title: DBG_ATTRIB_FLAGS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c8b3f52eff80c187d3c43b87cea804ace483169
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737560"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Описывает различные атрибуты интерфейса [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) или [Интерфейса IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md) Член [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.

## <a name="syntax"></a>Синтаксис

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Участники
 `DBG_ATTRIB_NONE`\
 Указывает, что атрибуты отсутствуют.

 `DBG_ATTRIB_ALL`\
 Отосеял все атрибуты.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Указывает, что ссылка или свойство имеет дочерние элементы.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Означает, что идентификатор для этого объекта был создан.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Означает, что идентификатор для этого объекта может быть создан.

 `DBG_ATTRIB_VALUE_READONLY`\
 Указывает, что значение доступно только для чтения.

 `DBG_ATTRIB_VALUE_ERROR`\
 Означает, что значение является ошибкой.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Указывает на то, что оценка имела побочный эффект.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Указывает, что это свойство действительно является контейнером перегрузок.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Указывает, что `DEBUG_PROPERTY_INFO::bstrValue` значение в Boolean.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Указывает, что `DEBUG_PROPERTY_INFO::bstrValue` значение в `TRUE`Является Boolean и .

 `DBG_ATTRIB_VALUE_INVALID`\
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` является недопустимым.

 `DBG_ATTRIB_VALUE_NAT`\
 Указывает, что `DEBUG_PROPERTY_INFO::bstrValue` значение в *"не вещь"*(NAT). NAT описывает флаг регистра в 64-битных процессорах Intel, который указывает на отложенные спекулятивные исключения.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Означает, что `DEBUG_PROPERTY_INFO::bstrValue` значение в возможно было автоматически расширено.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Означает, что оценка приурочена.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Означает, что `DEBUG_PROPERTY_INFO::bstrValue` значение в может быть представлено сырой строкой.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Означает, что это свойство имеет по крайней мере один пользовательский зритель, связанный с ним.

 `DBG_ATTRIB_ACCESS_NONE`\
 Указывает объект, который `public` `private`не `protected` имеет ни доступа, ни ввода.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Указывает объект, имеющий общий доступ.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Указывает объект, имеющий закрытый доступ.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Указывает объект, имеющий защищенный доступ.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Указывает объект, имеющий финальный доступ.

 `DBG_ATTRIB_ACCESS_ALL`\
 Маска для извлечения `DBG_ATTRIB_FLAGS`атрибутов доступа из .

 `DBG_ATTRIB_STORAGE_NONE`\
 Означает, что нет указанного типа хранилища.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Указывает глобальное хранилище.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Указывает статическое хранилище.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Указывает на хранение в регистре.

 `DBG_ATTRIB_STORAGE_ALL`\
 Маска для извлечения `DBG_ATTRIB_FLAGS`атрибутов хранения из .

 `DBG_ATTRIB_TYPE_NONE`\
 Означает, что нет модификатора типа.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Означает, что тип объекта является виртуальным.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Указывает, что тип объекта является константой.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Означает, что тип объекта синхронизирован.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Означает, что тип объекта является нестабильным.

 `DBG_ATTRIB_TYPE_ALL`\
 Маска для извлечения `DBG_ATTRIB_FLAGS`атрибутов типа из .

 `DBG_ATTRIB_DATA`\
 Означает, что этот объект является полем данных.

 `DBG_ATTRIB_METHOD`\
 Означает, что этот объект является методом.

 `DBG_ATTRIB_PROPERTY`\
 Означает, что этот объект является свойством.

 `DBG_ATTRIB_CLASS`\
 Означает, что этот объект является классом.

 `DBG_ATTRIB_BASECLASS`\
 Означает, что этот объект является базовым классом.

 `DBG_ATTRIB_INTERFACE`\
 Означает, что этот объект является интерфейсом.

 `DBG_ATTRIB_INNERCLASS`\
 Означает, что этот объект является внутренним классом.

 `DBG_ATTRIB_MOSTDERIVED`\
 Означает, что этот объект является *«наиболее полученным».* Термин *«наиболее полученный»* означает фактический тип объекта, а не тип его ссылки.

 `DBG_ATTRIB_CHILD_ALL`\
 Указывает маску `DBG_ATTRIB_DATA` `DBG_ATTRIB_MOSTDERIVED`через .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Означает, что объект имеет несколько пользовательских зрителей, связанных с ним.

## <a name="remarks"></a>Примечания

> [!NOTE]
> Значения в этом перечислении фактически не определены в сборке для C. Вместо этого необходимо скопировать определения в исходный файл.

 Эти флаги также используются для фильтрации детей объекта, например, при передавале в качестве аргумента [В.И.](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Значения могут быть объединены с `OR`bitwise .

 Флаг `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` является указанием [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] получить интерфейс [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) из интерфейса [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) и вызвать [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) для списка пользовательских зрителей.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
