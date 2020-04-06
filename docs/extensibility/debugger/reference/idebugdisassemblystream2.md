---
title: IDebugDisassemblyStream2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732045"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Этот интерфейс представляет собой поток инструкций.

## <a name="syntax"></a>Синтаксис

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя реализует этот интерфейс для поддержки разборки кода программы.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов на метод [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDisassemblyStream2`.

|Метод|Описание|
|------------|-----------------|
|[Прочитать](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Читает инструкции, начиная с текущего положения в потоке разборки.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Перемещает указатель чтения в потоке разборки определенное количество инструкций относительно заданной позиции.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Возвращает идентификатор местоположения кода для определенного контекста кода.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Возвращает объект контекста кода, соответствующий указанному идентификатору местоположения кода.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Возвращает идентификатор местоположения кода, представляющий текущее местоположение кода.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Получает исходный документ, связанный с этим потоком разборки.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Получает область действия этого потока разборки.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Получает размер этого потока разборки.|

## <a name="remarks"></a>Примечания
 Поток разборки может быть создан для представления всего адресного пространства или просто функции или модуля в пространстве. Каждая инструкция представлена структурой [DisassemblyData,](../../../extensibility/debugger/reference/disassemblydata.md) возвращенной вызовом на метод [Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
