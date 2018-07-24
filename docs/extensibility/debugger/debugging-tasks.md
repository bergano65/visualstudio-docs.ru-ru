---
title: Задачи отладки | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a1d2ae4b05398daa7c42be441cebecb304bf956
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204171"
---
# <a name="debug-tasks"></a>Отладка задач
Чтобы отладить программу, необходимо запустить и модуля отладки (DE) должен быть подключен к нему, иначе DE должен быть подключен к ранее запущенные программы. После присоединения DE необходимо создать определенные события запуска. В ответ отладочный пакет пытается выполнить привязку точки останова, заданные в интегрированной среде разработки. Когда программа достигает связанная точка останова, он прерывается и ждет ввод пользователя.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Проблемы безопасности](../../extensibility/debugger/security-issues.md)  
 Описание действия безопасности, которые необходимы для отладки программы.  
  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)  
 Содержит пошаговые инструкции по указанию DE, который вызывает операционной системы, чтобы запустить программу.  
  
 [Присоединиться к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Описывает процесс, используемый для отладки программы, в процессе, который уже выполняется.  
  
 [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Перечислены события, происходящие после DE присоединяется к программе, пока программа не в основной точки входа и готов для отладки.  
  
 [Элемент управления выполнения](../../extensibility/debugger/control-of-execution.md)  
 Объясняет, как DE обычно отправляет событие точки входа, событие завершения нагрузки или событии остановки, в зависимости от обстоятельств.  
  
 [Привязка точки останова](../../extensibility/debugger/binding-breakpoints.md)  
 Описывает, как это сделать, если пользователь устанавливает точку останова, среда IDE формирует запрос и запрашивает у сеанса отладки, чтобы создать точку останова.  
  
 [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
 Объясняет, как создавать выражения и что происходит при вычислении выражения.  
  
 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Объясняет, как с помощью вычислителя выражений (EE) поддерживаются визуализаторов типов и пользовательских средств просмотра.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Обзор компонентов Visual Studio отладки, включающие DE, EE и обработчик символов (SH).  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как DE действует одновременно в рамках кода, документацию и контекстов вычисления выражения. Описание для каждого из трех контекстов, расположение, положения или оценки, относящиеся к его.  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)