---
title: Включение отладки программы | Документация Майкрософт
description: Узнайте, как запустить модуль отладки или присоединить модуль отладки к существующей программе для отладки программы.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ac9a43a0ec539dd978710c23c9b44f27eac81799
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915262"
---
# <a name="enable-a-program-to-be-debugged"></a>Включение отладки программы
Прежде чем модуль отладки (DE) сможет выполнить отладку программы, необходимо сначала запустить DE или присоединить его к существующей программе.

## <a name="in-this-section"></a>В этом разделе
 [Получение порта](../../extensibility/debugger/getting-a-port.md) Описывает, как получить порт в качестве первого шага, чтобы включить отладку программы.

 [Регистрация программы](../../extensibility/debugger/registering-the-program.md) Описание следующего шага при включении отладки программы: ее регистрация в порте. После регистрации программу можно отлаживать в процессе присоединения или JIT-отладки.

 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md) Описание следующего шага: присоединение отладчика к программе.

 [Присоединение на основе запуска](../../extensibility/debugger/launch-based-attachment.md) Описывает вложение на основе запуска для программы, которое выполняется автоматически при запуске SDM.

 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md) Пошаговые инструкции по созданию обработчика отладки (DE) и присоединению его к программе.

## <a name="related-sections"></a>Связанные разделы
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Определяет модуль отладки (DE) и описывает службы, реализованные через интерфейсы DE, а также способ перехода отладчика между различными операционными режимами.
