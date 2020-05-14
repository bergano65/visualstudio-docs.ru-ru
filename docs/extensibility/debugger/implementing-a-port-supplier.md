---
title: Внедрение поставщика порта (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738557"
---
# <a name="implement-a-port-supplier"></a>Реализация поставщика порта
Поставщик порта поставляет порты по запросу менеджеру отладки сеанса (SDM). Поставщик порта должен быть реализован при отладке машины, не входящих в DCOM, или когда новое устройство требует поддержки. Например, чтобы обеспечить отладку сотового телефона, можно настроить поставщика порта, который предоставляет порты, которые подключаются к сотовому телефону (возможно, через ИК или сотовое соединение) и перечисляет процессы и программы, работающие на телефоне.

 Для отладки программ на компьютерах на базе Windows (включая удаленную отладку) Visual Studio предоставляет портовых поставщиков для процессов native and Common Language Runtime (CLR), поэтому в этих случаях нет необходимости настраивать собственного поставщика портов.

## <a name="in-this-section"></a>В этом разделе
 [Внедрение и регистрация поставщика порта](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Обсуждает, как SDM взаимодействует с поставщиком порта и его портами.

 [Необходимые интерфейсы портовых поставщиков](../../extensibility/debugger/required-port-supplier-interfaces.md) Документы интерфейсы, которые вы должны реализовать, чтобы получить поставщика порта.

## <a name="related-sections"></a>См. также
 [Концепции debugger](../../extensibility/debugger/debugger-concepts.md) Описывает основные архитектурные концепции отладки.

## <a name="see-also"></a>См. также
 [Эффектная студия отладчика расширяемые](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
