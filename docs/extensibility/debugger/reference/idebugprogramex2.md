---
title: IDebugProgramEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8961ea105779674aab0b67c9ad6339ce1c282f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722328"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Этот интерфейс позволяет диспетчеру отладки сеансов (SDM) присоединяться к программе и получать узел программы, связанный с программой.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский поставщик порта реализует этот интерфейс на том же объекте, что и интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , чтобы позволить модели SDM присоединяться к программе одновременно с тем, чтобы поставщик порта мог относить все сеансы, подключенные к программе. Поставщик настраиваемого порта может реализовать этот интерфейс, если он выбрал.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Модель SDM вызывает [QueryInterface](/cpp/atl/queryinterface) на `IDebugProgram2` интерфейсе, чтобы получить этот интерфейс для наблюдения за сеансами, подключенными к программам.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramEx2` .

|Метод|Описание|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Присоединяет программу к сеансу.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Возвращает узел программы, связанный с программой.|

## <a name="remarks"></a>Remarks
 Этот интерфейс является частным между SDM и программой.

## <a name="requirements"></a>Требования
 Заголовок: Портприв. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
