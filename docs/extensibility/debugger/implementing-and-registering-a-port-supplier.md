---
title: Реализация и регистрация поставщика порта | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10e68f06cde3cd562b145bd64f94581c65f7d7f6
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231650"
---
# <a name="implement-and-register-a-port-supplier"></a>Реализация и регистрация поставщика порта
Для отслеживания и указать порты, которые в свою очередь управления процессами — роль поставщика порта. Если порт должен быть создан, поставщика порта создается экземпляр с помощью CoCreate с идентификатором GUID поставщика порта (диспетчер отладки сеансов [SDM] будет использовать поставщика порта, который выбрал пользователь или поставщика порта указан в системе проекта). Затем вызывает SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) для просмотра, можно ли добавить какие-либо порты. Можно ли добавить порт, путем вызова запрашивается новый порт [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) и передавая ему [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , описывающий порт. `AddPort` Возвращает новый порт, представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс.  
  
## <a name="discussion"></a>Обсуждение  
 Порт создается путем поставщика порта, связанный с сервером машины или отладки. Сервер перечисляет ее поставщики порт, через[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) метод и поставщика порта перечисляет его портов через [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) метод.  
  
 В дополнение к обычной регистрации COM поставщика порта необходимо зарегистрироваться с помощью Visual Studio, поместив его имя и идентификатор CLSID в расположениях реестра. Вызывается вспомогательная функция отладки пакета SDK `SetMetric` обрабатывает переложить всю работу: она вызывается один раз для каждого элемента, для регистрации, таким образом:  
  
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
  
 Поставщика порта отменяет свою регистрацию путем вызова `RemoveMetric` (Вспомогательная функция другой пакет SDK для отладки) один раз для каждого элемента, который был зарегистрирован, таким образом:  
  
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
>  [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` и `RemoveMetric` статические функции определены в *dbgmetric.h* и скомпилированных в *ad2de.lib*. `metrictypePortSupplier`, `metricCLSID`, И `metricName` вспомогательные функции также определены в *dbgmetric.h*.  
  
 Поставщика порта можно указать его имя и идентификатор GUID, посредством методов [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) и [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), соответственно.  
  
## <a name="see-also"></a>См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)