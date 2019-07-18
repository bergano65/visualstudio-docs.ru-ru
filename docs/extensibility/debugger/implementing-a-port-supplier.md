---
title: Реализация поставщика порта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd5ba2a96b94cce65dc901a523232b1c3e0a45b9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349990"
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