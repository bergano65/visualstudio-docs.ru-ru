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
ms.openlocfilehash: 5d6875baf72d94494a1abaea9260e344b236f83c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685928"
---
# <a name="implement-a-port-supplier"></a>Реализация поставщика порта
Поставщика порта предоставляет порты на запрос на диспетчер отладки сеансов (SDM). Поставщика порта должен быть реализован, при отладке на машине не DCOM, или когда новое устройство требует поддержки. Например чтобы обеспечивать отладку для сотовых телефонов, можно настроить порт поставщика, который предоставляет порты, которые соединиться с мобильного телефона (возможно, посредством среды выполнения Интеграции или подключение ячейки) и перечисляет процессы и программы, работающие на телефоне.

 Для отладки программ на компьютерах, на базе Windows (включая удаленную отладку) Visual Studio предоставляет поставщикам портов для машинный код и процессов Common Language Runtime (CLR), поэтому нет необходимости для настройки собственного поставщика порта в таких случаях.

## <a name="in-this-section"></a>Содержание раздела
 [Реализация и регистрация поставщика порта](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) рассматриваются как SDM взаимодействует с поставщика порта и его портов.

 [Необходимые интерфейсы поставщика порта](../../extensibility/debugger/required-port-supplier-interfaces.md) Документирует интерфейсов, необходимо реализовать для получения поставщика порта.

## <a name="related-sections"></a>Связанные разделы
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md) описывает основные архитектурные понятия отладки.

## <a name="see-also"></a>См. также
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)