---
title: Включение программы для отладки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738896"
---
# <a name="enable-a-program-to-be-debugged"></a>Включить отладку программы
Прежде чем ваш отладка двигателя (DE) может отладить программу, вы должны сначала запустить DE или прикрепить его к существующей программе.

## <a name="in-this-section"></a>В этом разделе
 [Получить порт](../../extensibility/debugger/getting-a-port.md) Обсуждается, как получить порт в качестве первого шага к возможности отладки программы.

 [Регистрация программы](../../extensibility/debugger/registering-the-program.md) Объясняет следующий шаг в обеспечении отладки программы: регистрация ее в порту. После регистрации программа может быть отлажена либо в процессе присоединения, либо просто в срок (JIT) отладки.

 [Прикрепите к программе](../../extensibility/debugger/attaching-to-the-program.md) Объясняет следующий шаг: присоединение отладчика к программе.

 [Присоединение на основе запуска](../../extensibility/debugger/launch-based-attachment.md) Описывает приложение на основе запуска к программе, которое происходит автоматически при запуске SDM.

 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md) Шаги вас через необходимые события при создании отладки двигателя (DE) и прикрепляя его к программе.

## <a name="related-sections"></a>См. также
 [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Определяет движок отладки (DE) и описывает службы, реализованные через интерфейсы DE, и как они могут привести к переходу отладки между различными режимами работы.
