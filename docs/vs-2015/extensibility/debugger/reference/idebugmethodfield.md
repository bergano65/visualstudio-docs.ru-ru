---
title: IDebugMethodField | Документация Майкрософт
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
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09161f400b2917aeff4c79ba58a813a98e6b5f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569191"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugMethodField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmethodfield).  
  
Этот интерфейс описывает метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс. Этот интерфейс является специализацией, которая представляет метод.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс, если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_METHOD`. Кроме того, методы, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), и [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), возвращают `IDebugMethodField` интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсы, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Создает перечислитель для параметров метода.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Получает указатель «this» объект, содержащий метод.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Создает перечислитель для всех локальных переменных метода.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Создает перечислитель для выбранного локальные переменные метода.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Определяет, было ли определено определенного настраиваемого атрибута.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Создает перечислитель для Статические локальные переменные метода.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Возвращает контейнер глобального метода.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Создает перечислитель для тип каждого аргумента, необходимые для вызова метода.|  
  
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

