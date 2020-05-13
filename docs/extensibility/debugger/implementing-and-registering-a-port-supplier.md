---
title: Внедрение и регистрация поставщика порта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738529"
---
# <a name="implement-and-register-a-port-supplier"></a>Внедрение и регистрация поставщика порта
Роль портового поставщика заключается в отслеживании и поставке портов, которые, в свою очередь, управляют процессами. Когда порт должен быть создан, поставщик порта мгновенно использует CoCreate с GUID поставщика порта (менеджер отладки сеанса (SDM) будет использовать поставщика порта, выбранного пользователем, или поставщика порта, указанного проектной системой). Затем SDM вызывает [CanAddPort,](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) чтобы узнать, можно ли добавить порты. Если порт может быть добавлен, новый порт запрашивается, вызывая [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) и передавая его [IDebugPortRequest2,](../../extensibility/debugger/reference/idebugportrequest2.md) который описывает порт. `AddPort`возвращает новый порт, представленный интерфейсом [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md)

## <a name="discussion"></a>Обсуждение
 Порт создается поставщиком порта, который связан с машиной или сервером отладки. Сервер перечисляет своих портовых поставщиков методом[EnumPortSuppliers,](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) а поставщик порта перечисляет свои порты методом [EnumPorts.](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

 В дополнение к типичной регистрации COM, поставщик порта должен зарегистрироваться в Visual Studio, разместив свой CLSID и имя в конкретных местах реестра. Функция помощника Debugging SDK, называемая `SetMetric` обрабатывает эту работу: она называется один раз для регистрации каждого товара, таким образом:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Поставщик порта отрегистрируется, `RemoveMetric` позвонив (еще одна функция помощника Debugging SDK) один раз для каждого зарегистрированного товара, таким образом:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> Помощники [SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` и `RemoveMetric` статические функции, определенные в *dbgmetric.h* и составленные в *ad2de.lib*. , `metrictypePortSupplier` `metricCLSID`и `metricName` помощники также определены в *dbgmetric.h*.

 Поставщик порта может предоставить свое название и GUID методами [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) и [GetPortSupplierId,](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)соответственно.

## <a name="see-also"></a>См. также
- [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Помощники SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
