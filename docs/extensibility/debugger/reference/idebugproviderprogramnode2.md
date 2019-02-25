---
title: IDebugProviderProgramNode2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb717363266b95397ea749e7465b07df75f60da2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721853"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Этот интерфейс выполняет маршалинг интерфейса, связанных с программой через границы процессов.

## <a name="syntax"></a>Синтаксис

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс на тот же объект, реализующий [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки интерфейсов маршалинга через границы процессов.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProgramNode2` интерфейс для получения этого интерфейса. Если этот интерфейс не может быть получен, DE не поддерживает маршалинг интерфейсов.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание:|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Возвращает заданный интерфейс через границы процессов.|

## <a name="remarks"></a>Примечания
 Этот интерфейс реализуется в том случае, когда DE работает в отдельное пространство процесса из отлаживаемой программы: например, при выполнении DE в пространстве процесса Visual Studio, а не пространство процесса отлаживаемой программы.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)