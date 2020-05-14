---
title: ИдебугФилд Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728752"
---
# <a name="idebugfield"></a>IDebugField
Этот интерфейс представляет поле, то есть описание символа или типа.

## <a name="syntax"></a>Синтаксис

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс в качестве базового класса для всех полей.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс является базовым классом для всех полей. Основываясь на значении возврата [GetKind,](../../../extensibility/debugger/reference/idebugfield-getkind.md)этот интерфейс может вернуть более специализированные интерфейсы с помощью [queryInterface](/cpp/atl/queryinterface). Кроме того, многие `IDebugField` интерфейсы возвращают объекты из различных методов.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugField`.

|Метод|Описание|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Получает отображаемую информацию о символе или типе.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Получает вид поля.|
|[Gettype](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Получает тип поля.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Получает контейнер поля.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Получает адрес поля.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Получает размер поля, в байтах.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Получает расширенную информацию о поле.|
|[Равно](../../../extensibility/debugger/reference/idebugfield-equal.md)|Сравнивает два поля.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Получает независимую информацию о символе или типе.|

## <a name="remarks"></a>Примечания
 Тип эквивалентен языку `typedef`C.

 В следующем примере языка `weather` СЗ, является `sunny` тип `stormy` класса, и являются символами:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Представляет ли поле символ или тип, можно определить, позвонив [в GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) и изучив [результат FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md) Если `FIELD_KIND_TYPE` бит установлен, поле типа, и если `FIELD_KIND_SYMBOL` бит установлен, это символ.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
