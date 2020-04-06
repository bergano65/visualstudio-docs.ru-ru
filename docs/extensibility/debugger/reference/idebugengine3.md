---
title: IDebugEngine3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730653"
---
# <a name="idebugengine3"></a>IDebugEngine3
Представляет собой единый отладочный движок (DE), который контролирует отладку одного или нескольких модулей.

## <a name="syntax"></a>Синтаксис

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован пользовательским DE (если он поддерживает символы), чтобы включить состояние JustMyCode. Этот интерфейс должен быть реализован DE, если он поддерживает символы и JustMyCode.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс вызывается менеджером отладки сеанса (SDM) для передачи пользовательских опций для мест, из которых для загрузки символов. Он также называется установить GUID двигателя, когда он мгновенно (это GUID основан на метриках с момента регистрации двигателя). SDM также вызывает этот интерфейс для установки состояния JustMyCode и для установки всех исключений, известных отладчиком, в указанное состояние.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных от `IDebugEngine3` [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md)интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Устанавливает путь или пути, которые DE будет использовать для поиска символов отладки.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Загружает символы для всех модулей, которые еще не были загружены их символы.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Сообщает DE информацию о JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Устанавливает DE GUID из метрик.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Установите все исключения, которые в настоящее время невыплачены, в определенном состоянии.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
