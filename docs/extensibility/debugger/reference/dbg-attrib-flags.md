---
title: "DBG_ATTRIB_FLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DBG_ATTRIB_FLAGS
helpviewer_keywords: DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b1522f1b036efbedb62f625847d0ef1d60a95a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="dbgattribflags"></a>DBG_ATTRIB_FLAGS
Описывает различные атрибуты для [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) или [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) интерфейса. Член [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.  
  
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
  
## <a name="members"></a>Члены  
 DBG_ATTRIB_NONE  
 Указывает, что атрибуты отсутствуют.  
  
 DBG_ATTRIB_ALL  
 Указывает все атрибуты.  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 Указывает, что ссылка или свойство имеет дочерние элементы.  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 Указывает, что был создан код для этого объекта.  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 Указывает, что можно создать идентификатор для этого объекта.  
  
 DBG_ATTRIB_VALUE_READONLY  
 Указывает, что значение доступно только для чтения.  
  
 DBG_ATTRIB_VALUE_ERROR  
 Указывает, что значение является ошибкой.  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 Означает, что вычисления имеет побочный эффект.  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 Указывает, что это свойство действительно является контейнером для перегрузки.  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` является логическое значение.  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` является логическим и `TRUE`.  
  
 DBG_ATTRIB_VALUE_INVALID  
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` является недопустимым.  
  
 DBG_ATTRIB_VALUE_NAT  
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` — «*не самое*» (NAT). NAT описаны в 64-разрядных процессоров Intel регистра флаг, указывающий отложенное наблюдающей исключения.  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` возможно был автоматически развернут.  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 Указывает, что оценку истекло.  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 Указывает, что значение в `DEBUG_PROPERTY_INFO::bstrValue` может быть представлен необработанные строковые.  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 Указывает, что это свойство имеет по крайней мере одно пользовательское средство просмотра, связанные с ним.  
  
 DBG_ATTRIB_ACCESS_NONE  
 Указывает объект, ни `public`, `private`, ни `protected` тип доступа.  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 Указывает объект, имеющий общий доступ.  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 Указывает объект, имеющий закрытый доступ.  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 Указывает объект, имеющий защищенный доступ.  
  
 DBG_ATTRIB_ACCESS_FINAL  
 Указывает объект, имеющий финальный доступ.  
  
 DBG_ATTRIB_ACCESS_ALL  
 Маска для извлечения атрибутов доступ из `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_STORAGE_NONE  
 Указывает тип хранилища, не указан.  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 Указывает глобальное хранилище.  
  
 DBG_ATTRIB_STORAGE_STATIC  
 Указывает статическое хранилище.  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 Указывает хранилище в регистре.  
  
 DBG_ATTRIB_STORAGE_ALL  
 Маска для извлечения атрибутов из хранилища `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_TYPE_NONE  
 Указывает, что нет никакой модификатор типа.  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 Указывает, что тип объекта является виртуальным.  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 Указывает, что тип объекта является константой.  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 Указывает, что синхронизирована тип объекта.  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 Указывает, что тип объекта является временным.  
  
 DBG_ATTRIB_TYPE_ALL  
 Маска для извлечения типа атрибутов из `DBG_ATTRIB_FLAGS`.  
  
 DBG_ATTRIB_DATA  
 Указывает, что этот объект является полем данных.  
  
 DBG_ATTRIB_METHOD  
 Указывает, что этот объект является методом.  
  
 DBG_ATTRIB_PROPERTY  
 Указывает, что этот объект является свойством.  
  
 DBG_ATTRIB_CLASS  
 Указывает, что этот объект является классом.  
  
 DBG_ATTRIB_BASECLASS  
 Указывает, что этот объект базового класса.  
  
 DBG_ATTRIB_INTERFACE  
 Указывает, что этот объект является интерфейсом.  
  
 DBG_ATTRIB_INNERCLASS  
 Указывает, что этот объект внутреннего класса.  
  
 DBG_ATTRIB_MOSTDERIVED  
 Указывает, что этот объект "*замыкающего*". Термин «*замыкающего*» означает фактический тип объекта, а не тип его ссылки.  
  
 DBG_ATTRIB_CHILD_ALL  
 Указывает маску `DBG_ATTRIB_DATA` через `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 Указывает, что объект имеет несколько пользовательских средств просмотра, связанные с ним.  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Значения в этом перечислении фактически не определены в сборке, для C#. Вместо этого необходимо скопировать файл исходного определения.  
  
 Эти флаги также используются для фильтрации дочерних элементов объекта, например, при передаче в качестве аргумента для [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Значения могут объединяться с битовой `OR`.  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` Флаг, указывает на то, чтобы [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] для получения [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс из [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) интерфейс и вызова [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) список пользовательских средств просмотра.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)