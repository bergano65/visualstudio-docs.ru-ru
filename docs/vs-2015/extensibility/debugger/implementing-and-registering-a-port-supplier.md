---
title: Реализация и регистрация поставщика порта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430263"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Реализация и регистрация поставщика порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Для отслеживания и указать порты, которые в свою очередь управления процессами — роль поставщика порта. В то время, необходимо создать порт поставщика порта создается с помощью CoCreate с идентификатором GUID поставщика порта (диспетчер отладки сеансов [SDM] будет использовать поставщика порта выбрал пользователь или поставщика порта, указанного в системе проекта). Затем вызовет SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) для просмотра, можно ли добавить какие-либо порты. Можно ли добавить порт, путем вызова запрашивается новый порт [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) и передавая ему [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , описывающий порт. `AddPort` Возвращает новый порт, представленный [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) интерфейс.  
  
## <a name="discussion"></a>Обсуждение  
 Порт создается путем поставщика порта, который в свою очередь связан с сервером машины или отладки. Сервер можно перечислить его поставщикам портов через[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) метод и поставщика порта можно перечислить его порты, через [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) метод.  
  
 В дополнение к обычной регистрации COM поставщика порта необходимо зарегистрироваться с помощью Visual Studio, поместив его имя и идентификатор CLSID в расположениях реестра. Вызывается вспомогательная функция отладки пакета SDK `SetMetric` обрабатывает переложить всю работу: она вызывается один раз для каждого элемента, для регистрации, таким образом:  
  
```cpp#  
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
  
```cpp#  
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
> [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` и `RemoveMetric` являются статические функции определены в dbgmetric.h и компилируются в ad2de.lib. `metrictypePortSupplier`, `metricCLSID`, И `metricName` вспомогательные функции также определены в dbgmetric.h.  
  
 Поставщика порта можно указать его имя и идентификатор GUID, посредством методов [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) и [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), соответственно.  
  
## <a name="see-also"></a>См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Вспомогательные пакеты SDK для отладки](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Поставщики портов](../../extensibility/debugger/port-suppliers.md)
