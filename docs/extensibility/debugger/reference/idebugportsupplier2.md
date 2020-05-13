---
title: IDebugPortSupplier2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724471"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Этот интерфейс поставляет порты менеджеру отладки сеанса (SDM).

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
Поставщик пользовательских портов реализует этот интерфейс, чтобы представлять поставщика порта.

## <a name="notes-for-callers"></a>Заметки для абонентов
Звонок `CoCreateInstance` с поставщиком порта `GUID` возвращает этот интерфейс (это типичный способ получить этот интерфейс). Пример:

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

Звонок [в GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) возвращает этот интерфейс, представляющий текущего поставщика порта, используемого [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) возвращает этот интерфейс, представляя поставщика порта, который создал порт.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) представляет собой `IDebugPortSupplier` список `IEnumDebugPortSuppliers` интерфейсов (интерфейс получен от [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), представляющих [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]всех портовых поставщиков, зарегистрированных в).

Двигатель отладки обычно не взаимодействует с поставщиком порта.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDebugPortSupplier2`.

|Метод|Описание|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Получает название поставщика порта.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Получает идентификатор поставщика порта.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Получает порт от поставщика порта.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Перечисляет уже существующие порты.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Проверяет, что поставщик порта поддерживает добавление новых портов.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Добавляет порт.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Удаляет порт.|

## <a name="remarks"></a>Примечания
Поставщик порта может идентифицировать себя по имени и идентификатору, добавлять и удалять порты и перечислять все порты, которые предоставляет поставщик порта.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
