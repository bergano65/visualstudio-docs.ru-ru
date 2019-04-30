---
title: Включение программы для отладки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f301de66421ef1327b86d900305cb4ecbfb5623
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889698"
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