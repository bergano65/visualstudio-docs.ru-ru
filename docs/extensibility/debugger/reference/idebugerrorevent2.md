---
title: IDebugErrorEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 945b04fc2d5a370ef4b2d17abd90e6bdaa818553
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327661"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Этот интерфейс задает сообщение об ошибке возвращаются пользователю.

## <a name="syntax"></a>Синтаксис

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для сообщения об ошибках как доступное для чтения сообщения. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события, чтобы сообщить об ошибке. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, если он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|`GetErrorMessage`|Возвращает сообщение об ошибке в понятном виде.|

## <a name="remarks"></a>Примечания
 Если отладчик обнаруживает ошибку, этот интерфейс можно использовать чтобы сообщить пользователю сообщение через Visual Studio.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)