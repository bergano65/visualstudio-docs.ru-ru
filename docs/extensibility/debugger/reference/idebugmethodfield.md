---
title: "IDebugMethodField | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField
helpviewer_keywords: IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 818fdbcf236a1965eb1ea657f65a9d28421b42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Этот интерфейс описывает метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейса. Этот интерфейс является специализацией, которая представляет метод.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](/cpp/atl/queryinterface) получить этот интерфейс из [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_METHOD`. Кроме того, методы, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), и [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), возвращают `IDebugMethodField` интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсах, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Создает перечислитель для параметров метода.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Возвращает объект, содержащий метод указатель «this».|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Создает перечислитель для всех локальных переменных метода.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Создает перечислитель для выбранного локальных переменных метода.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Определяет, было ли определено определенного настраиваемого атрибута.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Создает перечислитель для статических локальных переменных метода.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Получает контейнер глобального метода.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Создает перечислитель для типа каждый аргумент, необходимый для вызова метода.|  
  
## <a name="remarks"></a>Примечания  
 Метод может содержать параметры, а также локальные переменные.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)