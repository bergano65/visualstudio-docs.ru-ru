---
title: IDebugProviderProgramNode2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720678"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Этот интерфейс маршалов программы, связанные с интерфейсами через границы процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс на том же объекте, который реализует [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки интерфейсов маршалинга через границы процесса.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [queryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` на интерфейс, чтобы получить этот интерфейс. Если этот интерфейс не может быть получен, DE не поддерживает маршалинг интерфейсов.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Получает определенный интерфейс через границы процесса.|

## <a name="remarks"></a>Примечания
 Этот интерфейс реализуется, когда DE работает в отдельном пространстве процесса от отладки программы: например, когда DE работает в пространстве процесса Visual Studio вместо отладительной программы.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
