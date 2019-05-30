---
title: IDebugBinder3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97e3165be9d478d08f4de7eb623de5b93fd3433a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330867"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс обеспечивает доступ к типам, псевдонимы и пользовательский визуализатор служб.

## <a name="syntax"></a>Синтаксис

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки реализует этот интерфейс для поддержки псевдонимы пользовательский визуализатор и службы доступа к информации типа объекта.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс получает этот интерфейс с помощью [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, предоставляемых [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс, этот интерфейс реализует следующее:

|Метод|Описание|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Извлекает объект памяти, представляющий памяти, с которым связан этот объект.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Получает исключение, связанное с объектом (если таковые имеются),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Получает псевдонимы по имени|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Извлекает массив все псевдонимы для этого объекта|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Возвращает количество типов аргументов, связанный с данным объектом|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Извлекает список типов аргументов, связанный с данным объектом|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Возвращает интерфейс к службе визуализатора|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Преобразует адрес объекта или адрес памяти 64-разрядной памяти контекста.|

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)