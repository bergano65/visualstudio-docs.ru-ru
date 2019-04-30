---
title: IDebugPortNotify2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2427bfbc70c992cfcd41217aec56aa94d825faae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918173"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Этот интерфейс регистрирует или отменяет регистрацию программы, которые можно отлаживать с портом, в котором он выполняется на.

## <a name="syntax"></a>Синтаксис

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Поставщик настраиваемого порта реализует этот интерфейс для поддержки добавления и удаления программ из порта. Обычно он реализован в тот же объект, реализующий [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызов [QueryInterface](/cpp/atl/queryinterface) на `IDebugPort2` интерфейс возвращает этот интерфейс. Кроме того, вызов [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) возвращает этот интерфейс. Модуль отладки можно увидеть этот интерфейс в качестве параметра [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPortNotify2`.

|Метод|Описание|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Регистрирует порт, на котором он выполняется на программы, которые можно отлаживать.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Отменяет регистрацию программы, можно отлаживать из порт, к которому он работает под управлением.|

## <a name="remarks"></a>Примечания
 Не узнать, при загрузке или выгрузке программ отладки, пользовательский порт поставщик должен реализовывать этот интерфейс. Все программы, которые загружаются для отладки через определенный порт, отслеживаются с помощью этого интерфейса.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)