---
title: IDebugDefaultPort2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732313"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Этот интерфейс предоставляет несколько методов для доступа к серверу порта и средствам уведомления.

## <a name="syntax"></a>Синтаксис

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio реализует этот интерфейс, чтобы представить порт отладки для доступа к программам. Поставщик пользовательских портов также может реализовать этот интерфейс, если он обрабатывает удаленную отладку.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Аргумент методы на интерфейсе [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) поставляет этот интерфейс. Вызов [queryInterface](/cpp/atl/queryinterface) на [интерфейсе IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) также может получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 В дополнение к методам, определенным в [IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md)этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Получает интерфейс уведомления порта из этого порта.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Получает интерфейс на сервер, размещая этот порт.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Определяет, работает ли этот порт на локальной машине.|

## <a name="remarks"></a>Примечания
 Название «`IDebugDefaultPort2`немного неправильно, так как оно не представляет собой порт по умолчанию. Его можно назвать "IDebugPort3".

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
