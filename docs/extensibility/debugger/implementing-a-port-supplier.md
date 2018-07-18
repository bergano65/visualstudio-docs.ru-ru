---
title: Реализация поставщика порта | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0743f307dc579f6197880b0b89acaf2db0dda08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098996"
---
# <a name="implementing-a-port-supplier"></a>Реализация поставщика порта
Порт поставщика предоставляет порты на запрос к диспетчеру сеанса отладки (SDM). Поставщика порта должен быть реализован при отладке на компьютер без DCOM или если требуется поддержка нового устройства. Например для предоставления отладки для сотовых телефонов, необходимо реализовать порт поставщика, который предоставляет порты, которые подключаются мобильного телефона (возможно с помощью IR или ячейки подключения) и перечисляет процессы и программы, запущенные на телефоне.  
  
 Для отладки программ на компьютерах, на основе Windows (включая удаленную отладку) Visual Studio предоставляет поставщикам портов для машинного кода и процессы Common Language Runtime (CLR), поэтому нет необходимости реализовывать собственные поставщика порта в тех случаях.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Реализация и регистрация поставщика порта](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Описывает, как SDM взаимодействует с поставщика порта и его портов.  
  
 [Интерфейс поставщика необходимого порта](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Описываются интерфейсы, которые должны быть реализованы для получения поставщика порта.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные принципы отладки архитектуры.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)