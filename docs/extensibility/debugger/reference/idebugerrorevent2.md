---
title: IDebugErrorEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00fd8b4b42f11d18958f8a969bc4ccd58754ab93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729999"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Этот интерфейс определяет сообщение об ошибке, о чем можно сообщить пользователю.

## <a name="syntax"></a>Синтаксис

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы сообщать об ошибках как о читаемых человеком сообщениях. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект этого события для сообщения об ошибке. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) которая поставляется SDM при подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|`GetErrorMessage`|Возвращает ошибку в качестве читаемой человеком строки.|

## <a name="remarks"></a>Примечания
 Если движок отладки сталкивается с ошибкой, он может использовать этот интерфейс, чтобы сообщить сообщение через Visual Studio пользователю.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
