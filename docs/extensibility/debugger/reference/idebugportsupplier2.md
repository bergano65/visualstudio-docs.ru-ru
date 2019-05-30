---
title: IDebugPortSupplier2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 947a311cb1e83eaa131730725aeb7938e5615f0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340053"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Этот интерфейс предоставляет порты, чтобы диспетчер отладки сеансов (SDM).

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Пользовательский порт поставщик реализует этот интерфейс для представления поставщика порта.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Вызов `CoCreateInstance` с поставщика порта `GUID` возвращает этот интерфейс (это типичный способ получения этого интерфейса). Пример:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Вызов [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) возвращает этот интерфейс, представляющий текущий поставщик порта, используемый [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) возвращает этот интерфейс, представляющий поставщика порта, который создан порт.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) представляет список `IDebugPortSupplier` интерфейсы ( `IEnumDebugPortSuppliers` интерфейс получается из [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), представляющий всех поставщиков порт зарегистрировано [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).

Модуль отладки обычно не взаимодействует с поставщика порта.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugPortSupplier2`.

|Метод|Описание|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Получает имя поставщика порта.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Возвращает идентификатор поставщика порта.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Возвращает порт из поставщика порта.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Перечисляет порты, которые уже существуют.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Проверяет, что поставщик порта поддерживает добавление новых портов.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Добавляет порт.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Удаляет порт.|

## <a name="remarks"></a>Примечания
Поставщика порта можно идентифицировать себя имя и идентификатор, добавить и удалить порты и перечислить все порты, которые предоставляет поставщик порта.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
