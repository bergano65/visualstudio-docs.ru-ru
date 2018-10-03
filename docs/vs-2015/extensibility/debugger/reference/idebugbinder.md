---
title: IDebugBinder | Документация Майкрософт
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
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f322cf7351ec0d0a348ca06a07557127589973d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561086"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugBinder](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder).  
  
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс привязывает поле символа, обычно возвращаемые при помощи поставщик символов, к памяти контекста или объект, содержащий текущее значение символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс поддерживает вычисление выражений и должен быть реализован модуль отладки (DE).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс используется в процессе вычисления выражений и обычно используется в реализации [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBinder`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Получает контекст в памяти или объект, содержащий текущее значение символа.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Определяет тип времени выполнения объекта.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Преобразует адрес памяти или расположение объекта к контексту памяти.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Получает [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) объект, используемый для создания параметров функции.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Возвращает точный тип для переменной.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс возвращает объекты, которые используются средством оценки выражений в синтаксический анализ деревьев. Средство оценки выражений выполняет синтаксический анализ выражения с помощью поставщика символов для преобразования символов в выражении в экземпляры [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), которые описывают каждый символ, с точки зрения его типа и расположения в исходном коде. [Привязать](../../../extensibility/debugger/reference/idebugbinder-bind.md) метод преобразует `IDebugField` объектов [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты, которые подключиться или выполнить привязку символ типа в действительное значение в памяти. Эти `IDebugObject` объекты затем сохраняются в дерево синтаксического анализа для дальнейшего определения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)

