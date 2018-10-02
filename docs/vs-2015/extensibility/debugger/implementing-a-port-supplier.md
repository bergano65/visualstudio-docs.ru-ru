---
title: Реализация поставщика порта | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d14c2642d30ee46df0cd1b766540ae0b135e4d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571867"
---
# <a name="implementing-a-port-supplier"></a>Реализация поставщика порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [реализация поставщика порта](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-a-port-supplier).  
  
Поставщика порта предоставляет порты на запрос на диспетчер отладки сеансов (SDM). Поставщика порта должна быть реализована при отладке на компьютер без DCOM или если требуется поддержка нового устройства. Например чтобы обеспечивать отладку для сотовых телефонов, может реализовать поставщика порта, который обеспечивает порта, соединиться с мобильного телефона (возможно с помощью среды выполнения Интеграции или подключение ячейки) и перечисляет процессы и программы, работающие на телефоне.  
  
 Для отладки программ на компьютерах, на базе Windows (включая удаленную отладку) Visual Studio предоставляет поставщикам портов для машинный код и процессов Common Language Runtime (CLR), поэтому нет необходимости реализовать собственный поставщик порта в таких случаях.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Реализация и регистрация поставщика порта](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Описывает, как SDM взаимодействует с поставщика порта и его портов.  
  
 [Интерфейс поставщика необходимого порта](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Описываются интерфейсы, которые должны быть реализованы для получения поставщика порта.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

