---
title: "IDebugObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject"
helpviewer_keywords: 
  - "Интерфейс IDebugObject"
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет объект, который создает связыватель для инкапсуляции значения символов и выражения.  
  
## Синтаксис  
  
```  
IDebugObject : IUnknown  
```  
  
## Примечания для разработчиков  
 Вычислитель выражений реализует этот интерфейс для представления объекта.  
  
## Примечания для вызывающих объектов  
 Этот интерфейс является базовым классом для всех объектов, средство оценки выражений использует проанализированного выражения. Возвращается путем вызова [Привязка](../../../extensibility/debugger/reference/idebugbinder-bind.md) метод.[QueryInterface](/visual-cpp/atl/queryinterface) более специализированными интерфейсами получает из этого интерфейса.  
  
## Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugObject`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Возвращает размер объекта.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Возвращает значение объекта в виде последовательности байтов.|  
|[SetValue](../Topic/IDebugObject::SetValue.md)|Задает значение объекта из последовательности байтов.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Задает значение этого объекта ссылки.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Возвращает контекст памяти, представляющий адрес значения объекта.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Создает копию управляемого объекта в адресное пространство ядра отладки.|  
|[IsNullReference](../Topic/IDebugObject::IsNullReference.md)|Проверяет, является ли этот объект является пустой ссылкой.|  
|[IsEqual](../Topic/IDebugObject::IsEqual.md)|Сравнивает объект для данного объекта.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Определяет, является ли этот объект только для чтения.|  
|[Прокси](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Определяет, является ли объект прозрачный прокси.|  
  
## Заметки  
 Средство оценки выражений использует этот интерфейс в качестве базового класса для представления объектов в дерево синтаксического анализа.  
  
## Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../Topic/IDebugArrayObject::GetElement.md)   
 [Привязка](../../../extensibility/debugger/reference/idebugbinder-bind.md)