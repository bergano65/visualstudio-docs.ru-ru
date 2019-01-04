---
title: IDebugFunctionObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d352870800a7b5e7fc1408d607a24f616b0f22d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954173"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс представляет функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFunctionObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Вычислитель выражений реализует этот интерфейс, представляющий функцию.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс является специализацией [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) интерфейс и получается с помощью [QueryInterface](/cpp/atl/queryinterface) на `IDebugObject` интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` интерфейс предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Создает объект примитивы.|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Создает объект, с помощью конструктора.|  
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Создает объект с помощью отсутствует конструктор.|  
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Создает объект массива.|  
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Создает объект string.|  
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Вызывает функцию и возвращает результирующее значение как объект.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс позволяет вычислитель выражений для представления функций в дерево синтаксического анализа. `Create` Методы этого интерфейса используются для создания объектов, представляющих входные параметры метода. Функция затем может быть выполнена путем вызова [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) метод, который возвращает объект, представляющий возвращаемое значение функции.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)