---
title: IDebugObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4cff859d2aa4b3a3c88978e077102e045efe1f3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет объект, который создает связыватель для инкапсуляции значения символов и выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Вычислитель выражений реализует этот интерфейс для представления объекта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс является базовым классом для всех объектов, средство оценки выражений использует в синтаксического анализа выражения. Он возвращается путем вызова [привязки](../../../extensibility/debugger/reference/idebugbinder-bind.md) метод. [QueryInterface](/cpp/atl/queryinterface) получает более специализированных интерфейсов из этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugObject`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Возвращает размер объекта.|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Возвращает значение объекта в виде последовательных последовательность байтов.|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Задает значение объекта из последовательных последовательность байтов.|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Задает значение ссылки из этого объекта.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Возвращает контекст памяти, представляющий адрес значения объекта.|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Создает копию объекта управляемого объекта в адресном пространстве ядро отладки.|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Проверяет, является ли этот объект является пустой ссылкой.|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Сравнивает объект на эту функцию.|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Определяет, является ли этот объект только для чтения.|  
|[Прокси](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Определяет, является ли объект прозрачного прокси.|  
  
## <a name="remarks"></a>Примечания  
 Средство оценки выражений использует этот интерфейс в качестве базового класса для представления объектов в дерево синтаксического анализа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md)