---
title: "IDebugMethodField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField"
helpviewer_keywords: 
  - "Интерфейс IDebugMethodField"
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMethodField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс описывает метод.  
  
## Синтаксис  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## Примечания по реализации  
 Поставщик символов реализует этот интерфейс на одном и том же объекта, реализующего [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс.  Этот интерфейс специализация, которая представляет метод.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) если интерфейс  [GetKind](../Topic/IDebugField::GetKind.md) возвращает  `FIELD_TYPE_METHOD`.  Кроме того, методы [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)"  [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)и  [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)все возвращающие  `IDebugMethodField` интерфейс.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и  [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсы этот интерфейс реализуется следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Создает перечислитель для параметров метода.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Возвращает "" указатель объекта, содержащего данный метод.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Создает перечислитель для всех локальных переменных метода.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Создает перечислитель для выбранных локальных переменных метода.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Определяет, определен ли указанный настраиваемый атрибут.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Создает перечислитель для статических локальных переменных метода.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Получает глобальный контейнер метода.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Создает перечислитель для каждого необходимого типа аргумента, чтобы вызвать метод.|  
  
## Заметки  
 Метод может содержать параметры, а также локальные переменные.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)