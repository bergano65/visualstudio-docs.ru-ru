---
title: IEnumDebugReferenceInfo2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28e10da879427f885e0af0109e3a701e4fcb44ec
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223250"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Этот интерфейс перечисляет [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структуры.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс как часть его поддержка ссылок на объекты в памяти. Этот интерфейс должен быть реализован только в том случае, если поддерживаются ссылки.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Visual Studio вызывает [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugReferenceInfo2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Извлекает указанное число [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Пропускает заданное число [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Получает число [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) структур в перечислителе.|

## <a name="remarks"></a>Примечания
 Ссылка — по существу тип и адрес, а свойство — имя, тип и адрес. Ссылка сохраняется до тех пор, пока объект называется существует в памяти. См. в разделе [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) для получения дополнительных сведений.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)