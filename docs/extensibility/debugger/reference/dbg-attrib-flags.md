---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "Перечисления DBGPROP_ATTRIB_FLAGS"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает различные атрибуты [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) или  [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) интерфейс.  Элемент [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структура.  
  
## Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
## Члены  
 DBG\_ATTRIB\_NONE  
 Указывает атрибуты.  
  
 DBG\_ATTRIB\_ALL  
 Отображает все атрибуты.  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 Указывает, что ссылка или свойства имеют дочерних элементов.  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 Указывает, что было создано идентификатор для данного объекта.  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 Указывает на то, что идентификатор для данного объекта могут быть созданы.  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 Указывает, что значение только для чтения.  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 Указывает, что ошибка.  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 Указывает, что вычисление имеет побочный эффект.  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 Указывает, что данное свойство действительно контейнер перегрузок.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 Указывает, что значения в `DEBUG_PROPERTY_INFO::bstrValue` логический.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 Указывает, что значения в `DEBUG_PROPERTY_INFO::bstrValue` логическое и  `TRUE`.  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 Указывает, что значения в `DEBUG_PROPERTY_INFO::bstrValue` недопустимый.  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 Указывает, что значения в `DEBUG_PROPERTY_INFO::bstrValue` "не самое"\(Nat\).  Преобразование сетевых адресов описывает пометить регистра в процессорах Intel 64, указывает отложенное умозрительные исключения.  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 Указывает, что значения в `DEBUG_PROPERTY_INFO::bstrValue` по возможности автоматическ\-развернет.  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 Указывает, что вычисление имеет синхронизированное\-вне.  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 Указывает, что значения в `DEBUG_PROPERTY_INFO::bstrValue` может быть представлено сырцовой строкой.  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 Указывает, что это свойство имеет по крайней мере одного настраиваемого средства просмотра, связанного с ним.  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 Указывает объект, который не имеет ни одного `public`"  `private`ни  `protected` доступ типа.  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 Указывает объект, имеющий открытого доступа.  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 Указывает объект, который содержит закрытый доступ.  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 Указывает объект, защищал доступ.  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 Указывает конечный объект, имеющий доступ.  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 Маска для извлечения атрибуты доступа из `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 Указывает, что заданный тип хранения.  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 Указывает глобальная хранилище.  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 Указывает статического хранилища.  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 Указывает хранилище в регистре.  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 Маска для извлечения атрибуты хранилища из `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 Указывает, что никакой модификатор типа.  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 Отображает тип объекта виртуальным.  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 Указывает, что тип объекта.  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 Отображает тип объекта, синхронизирован.  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 Отображает тип объекта, испаряющ.  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 Маска для извлечения атрибуты типа из `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_DATA  
 Указывает, что данный объект поля данных.  
  
 DBG\_ATTRIB\_METHOD  
 Указывает, что данный объект метод.  
  
 DBG\_ATTRIB\_PROPERTY  
 Указывает, что данный объект свойства.  
  
 DBG\_ATTRIB\_CLASS  
 Указывает, что данный объект класса.  
  
 DBG\_ATTRIB\_BASECLASS  
 Указывает, что данный объект базовый класс.  
  
 DBG\_ATTRIB\_INTERFACE  
 Указывает, что данный объект интерфейса.  
  
 DBG\_ATTRIB\_INNERCLASS  
 Указывает, что данный объект внутренний класс.  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 Указывает, что данный объект \`*дополнительные всего\-выведено*'.  Термин "*дополнительные всего\-выведено*"означает фактический тип объекта, а не его тип ссылки.  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 Указывает маску `DBG_ATTRIB_DATA` via  `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 Указывает, что объект имеет нескольких пользовательских средств просмотра, связанных с ним.  
  
## Заметки  
  
> [!NOTE]
>  Значения в этом перечислении фактически не определенные в сборке для c\#.  Вместо этого необходимо скопировать определения к конкретному файлу источника.  
  
 Эти флаги также используются для фильтрации дочерние узлы объекта, например, передается в качестве аргумента [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md).  Значения могут объединяться с побитовый оператор `OR`.  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` пометить индикаторов к  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] доступ  [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс из  [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс и вызвать метод  [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) список пользовательских средств просмотра.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)