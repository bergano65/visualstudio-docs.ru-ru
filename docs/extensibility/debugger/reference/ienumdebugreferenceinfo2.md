---
title: IEnumDebugReferenceInfo2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715269"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Этот интерфейс перечисляет [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс как часть своей поддержки ссылок на объекты в памяти. Этот интерфейс должен быть реализован только при поддержке ссылок.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Visual Studio вызывает [EnumChildren,](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugReferenceInfo2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Извлекает определенное количество [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Пропускает определенное количество [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Получает количество [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в регистраторе.|

## <a name="remarks"></a>Примечания
 Ссылка по существу является типом и адресом, в то время как свойство — это имя, тип и адрес. Ссылка сохраняется до тех пор, пока объект, о котором идет речь, существует в памяти. Более подробную информацию можно узнать [в IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
