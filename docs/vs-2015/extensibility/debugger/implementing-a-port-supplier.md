---
title: Реализация поставщика порта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152675"
---
# <a name="implementing-a-port-supplier"></a>Реализация поставщика порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
