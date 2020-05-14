---
title: IDebugProgramEx2 Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722328"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Этот интерфейс позволяет диспетчеру отладки сеанса (SDM) прикрепить к программе и получить узло программы, связанное с программой.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс на том же объекте, что и интерфейс [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) чтобы позволить SDM прикрепить сяопродачку к программе и в то же время позволяет поставщику порта отслеживать все сеансы, прикрепленные к программе. Поставщик пользовательских портов может реализовать этот интерфейс, если он выбирает.

## <a name="notes-for-callers"></a>Заметки для абонентов
 SDM вызывает [queryInterface](/cpp/atl/queryinterface) `IDebugProgram2` на интерфейсе, чтобы получить этот интерфейс для отслеживания сеансов, которые прилагаются к программам.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramEx2`.

|Метод|Описание|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Прикрепляет программу к сеансу.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Получает узл программы, связанный с программой.|

## <a name="remarks"></a>Примечания
 Этот интерфейс является закрытым между SDM и программой.

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
