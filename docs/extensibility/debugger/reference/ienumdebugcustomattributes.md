---
title: IEnumDebugCustomAttributes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e706999595033ac76508eaa5e3b3f995839ceaea
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321559"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
Перечисляет настраиваемые атрибуты.

## <a name="syntax"></a>Синтаксис

```
IEnumCustomAttributes : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс для поддержки настраиваемых атрибутов (через [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) интерфейс).

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugCustomAttributes`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Извлекает указанное число настраиваемых атрибутов в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Пропускает указанное число настраиваемых атрибутов в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Получает число настраиваемых атрибутов в перечислителе.|

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)