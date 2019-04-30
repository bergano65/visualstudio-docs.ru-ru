---
title: IDebugDefaultPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e646a248e4b7da03a9dbad9bcea2470d9d0f450
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876014"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Этот интерфейс предоставляет несколько методов для работы порта сервера и средства уведомлений.

## <a name="syntax"></a>Синтаксис

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс для представления порта отладки для доступа к программам. Поставщика пользовательского порта также можно реализовать этот интерфейс, если производится обработка удаленной отладки.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Аргумент методам [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейс поддерживает этот интерфейс. Вызов [QueryInterface](/cpp/atl/queryinterface) на [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс можно также получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, определенных в [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Получает интерфейс уведомлений порт от данного порта.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Получает интерфейс, сервер, содержащий этот порт.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Определяет, выполняется ли этот порт на локальном компьютере.|

## <a name="remarks"></a>Примечания
 Имя "`IDebugDefaultPort2`» является немного неверно, так как он не представляет порт по умолчанию. Он может вызываться «IDebugPort3.»

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)