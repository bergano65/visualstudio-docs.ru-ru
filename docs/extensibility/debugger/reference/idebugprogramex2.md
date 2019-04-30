---
title: IDebugProgramEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99b57aece9b835ac1f2277fdd626a9fdff7b903f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916977"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Этот интерфейс позволяет сеанс отладки manager (SDM) присоединиться к программе и получить узел программы, связанный с программой.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский порт поставщик реализует этот интерфейс на один и тот же объект как [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, чтобы позволить SDM присоединиться к программе в том случае, когда в то же время позволяя поставщика порта для отслеживания всех сеансов подключен к программа. Если он выбирает поставщика пользовательского порта можно реализовать этот интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовы SDM [QueryInterface](/cpp/atl/queryinterface) на `IDebugProgram2` интерфейс для получения этого интерфейса позволяет отслеживать сеансы, которые были присоединены к программам.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramEx2`.

|Метод|Описание|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Присоединяет программу к сеансу.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Получает узел программы, связанный с программой.|

## <a name="remarks"></a>Примечания
 Этот интерфейс является закрытым между SDM и программой.

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)