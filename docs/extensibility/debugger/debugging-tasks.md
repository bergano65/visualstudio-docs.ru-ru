---
title: Задачи отладки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738955"
---
# <a name="debug-tasks"></a>Задачи дебуза
Чтобы отладить программу, она должна быть запущена и отладка двигателя (DE) должны быть прикреплены к нему, иначе DE должны быть прикреплены к ранее запущенной программе. После присоединения DE должен генерировать определенные события запуска. В ответ пакет отладки пытается связать точки разрыва, установленные в IDE. Когда программа попадает в точку разрыва, она останавливается и ждет ввода пользователя.

## <a name="in-this-section"></a>В этом разделе
 [Вопросы безопасности](../../extensibility/debugger/security-issues.md) Обсуждается шаги безопасности, необходимые для отладки программы.

 [Запуск программы](../../extensibility/debugger/launching-a-program.md) Предоставляет пошаговые инструкции о том, как указать DE, который вызывает операционную систему для запуска программы.

 [Прикрепите непосредственно к программе](../../extensibility/debugger/attaching-directly-to-a-program.md) Описывает процесс, используемый для отладки программы в процессе, который уже запущен.

 [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Перечисляет события, которые происходят после присоединения DE к программе, пока программа не находится в ее основной точке входа и не будет готова к отладке.

 [Контроль исполнения](../../extensibility/debugger/control-of-execution.md) Объясняет, как DE обычно отправляет событие начальной точки, событие с завершением нагрузки или событие остановки, в зависимости от обстоятельств.

 [Связать точки разрыва](../../extensibility/debugger/binding-breakpoints.md) Описывает, как, если пользователь устанавливает точку разрыва, IDE формулирует запрос и подсказывает сеанс отладки для создания точки разрыва.

 [Оценка выражений](../../extensibility/debugger/evaluating-expressions.md) Объясняет, как создаются выражения и что происходит при оценке выражения.

 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md) Объясняет, как визуализаторы типов и пользовательские зрители поддерживаются оценщиком выражения (EE).

## <a name="related-sections"></a>См. также
 [Концепции debugger](../../extensibility/debugger/debugger-concepts.md) Описывает основные архитектурные концепции отладки.

 [Компоненты debugger](../../extensibility/debugger/debugger-components.md) Предоставляет обзор компонентов отладки Visual Studio, которые включают DE, EE и обработчик символов (SH).

 [Контексты debugger](../../extensibility/debugger/debugger-contexts.md) Объясняет, как DE работает одновременно в контекстах оценки кода, документации и выражения. Описывает для каждого из трех контекстов место, положение или оценку, относящуюся к нему.

## <a name="see-also"></a>См. также
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
