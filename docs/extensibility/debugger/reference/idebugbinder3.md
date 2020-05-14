---
title: IDebugBinder3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa85872337fdc1f7519d0de98cffe1436ef41c67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735668"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс обеспечивает доступ к типам, псевдонимам и пользовательским услугам визуализатора.

## <a name="syntax"></a>Синтаксис

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка движок реализует этот интерфейс для поддержки псевдонимов, пользовательских служб визуализатора и доступа к информации типа объекта.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Интерфейс [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) получает этот интерфейс с помощью [queryInterface.](/cpp/atl/queryinterface)

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 В дополнение к методам, предоставляемым интерфейсом [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) этот интерфейс реализует следующие:

|Метод|Описание|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Извлекает объект памяти, представляющий память, к которой связан этот объект.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Извлекает исключение, связанное с этим объектом (если таковые имеется),|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Получает псевдоним, учитывая его имя,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Извлекает массив всех псевдонимов для этого объекта,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Получает количество типов аргументов, связанных с этим объектом,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Извлекает список типов аргументов, связанных с этим объектом,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Получает интерфейс службы визуализатора,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Преобразует месторасположение объекта или 64-битный адрес памяти в контекст памяти.|

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
