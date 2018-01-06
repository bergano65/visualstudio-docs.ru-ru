---
title: "Реализация поставщика порта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: aa70e2a6019a97c248e6d4b411dacc222be59a1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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