---
title: Реализация поставщика порта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e59ad83499e69bcf257ae212c18b14fba208f3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55025817"
---
# <a name="implement-a-port-supplier"></a>Реализация поставщика порта
Поставщика порта предоставляет порты на запрос на диспетчер отладки сеансов (SDM). Поставщика порта должен быть реализован, при отладке на машине не DCOM, или когда новое устройство требует поддержки. Например чтобы обеспечивать отладку для сотовых телефонов, можно настроить порт поставщика, который предоставляет порты, которые соединиться с мобильного телефона (возможно, посредством среды выполнения Интеграции или подключение ячейки) и перечисляет процессы и программы, работающие на телефоне.  
  
 Для отладки программ на компьютерах, на базе Windows (включая удаленную отладку) Visual Studio предоставляет поставщикам портов для машинный код и процессов Common Language Runtime (CLR), поэтому нет необходимости для настройки собственного поставщика порта в таких случаях.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Реализация и регистрация поставщика порта](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Описывает, как SDM взаимодействует с поставщика порта и его портов.  
  
 [Интерфейс поставщика необходимого порта](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Описываются интерфейсы, которые необходимо реализовать для получения поставщика порта.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)