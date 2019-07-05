---
title: Включение программы для отладки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b939b692e4e93243f5f346fcd2fcb2872e989615
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341643"
---
# <a name="enable-a-program-to-be-debugged"></a>Включение программы для отладки
Прежде, чем ваш модуль отладки (DE) можно отлаживать программы, необходимо сначала запустить DE или присоединить ее к существующей программы.

## <a name="in-this-section"></a>Содержание раздела
 [Назначить порт](../../extensibility/debugger/getting-a-port.md) описывается получение порта на первом этапе, чтобы Включение программы для отладки.

 [Регистрация программы](../../extensibility/debugger/registering-the-program.md) объясняется следующим шагом Включение программы для отладки: регистрировать его через порт. После регистрации можно отлаживать программы, процесс присоединения или отладки just-in-time (JIT).

 [Присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md) объясняет следующий шаг: присоединить отладчик к программе.

 [Присоединение основе запуска](../../extensibility/debugger/launch-based-attachment.md) описывает вложение на основе запуска для программы, которое выполняется автоматически при запуске, SDM.

 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md) пошагово продемонстрирует требуемых событий при создании модуля отладки (DE) и подключите его к программе.

## <a name="related-sections"></a>Связанные разделы
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) определяет модуля отладки (DE), а также описание служб, реализуемых через интерфейсы DE и как они могут вызвать отладчик для перехода между различные рабочие режимы.