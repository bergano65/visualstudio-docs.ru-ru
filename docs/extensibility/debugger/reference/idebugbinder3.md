---
title: IDebugBinder3 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6924cfb321ade3955c8e039e32a0374158ea43b6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс обеспечивает доступ к типам, псевдонимы и пользовательский визуализатор служб.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для поддержки псевдонимы, пользовательский визуализатор служб и доступ к данным типа объекта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс, получает этот интерфейс с помощью [QueryInterface](/cpp/atl/queryinterface).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, предоставляемых [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс, этот интерфейс реализует следующие:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Извлекает объект памяти, представляющий памяти, с которым связан этот объект.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Получает исключение, связанное с объектом (если есть)|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Возвращает псевдоним с заданным именем|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Извлекает массив все псевдонимы для этого объекта|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Возвращает количество типов аргументов, связанный с данным объектом|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Получает список типов аргументов, связанный с данным объектом|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Возвращает интерфейс к службе визуализатора|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Преобразует расположение объекта или адресе памяти 64-разрядных контекст памяти.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)