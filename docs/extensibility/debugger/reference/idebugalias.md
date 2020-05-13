---
title: ИдебугАлиас Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736513"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Представляет числовый псевдоним для переменной. Псевдоним — это просто другое название для переменной.

## <a name="syntax"></a>Синтаксис

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения (EE) реализует этот интерфейс для поддержки численных псевдонимов для переменных.

## <a name="notes-for-callers"></a>Заметки для абонентов
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) создает псевдоним для конкретного объекта. Для поиска псевдонимов используйте [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) или [GetAllAliases.](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В интерфейсе определены `IDebugAlias` следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Получает объект, к которому относится этот псевдоним.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Получает псевдоним имя.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Извлекает `ICorDebugValue` интерфейс, предоставляющий доступ к управляемой кодовой информации об этом объекте (только управляемый код).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Отметив этот псевдоним как не используемый.|

## <a name="remarks"></a>Примечания
 Псевдоним — это десятичное число в строковой форме, за которым следует, например, символ «символ 1001».

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
