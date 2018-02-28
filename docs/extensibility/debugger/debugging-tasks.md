---
title: "Отладка задачи | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d1a6ffff4d3ac0410ca3de7e2cd595119763e88b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-tasks"></a>Задачи отладки
Чтобы отладить программу, необходимо запустить и модуля отладки (DE) должен быть подключен к нему, иначе DE должен быть подключен к ранее запущенной программы. После присоединения, DE необходимо создать некоторые события запуска. В результате отладочный пакет пытается выполнить привязку точки останова, заданные в Интегрированной среде разработки. Когда программа достигает связанная точка останова, он прекращает работу и ожидает ввода данных пользователем.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Проблемы безопасности](../../extensibility/debugger/security-issues.md)  
 Описание действия безопасности, необходимые для отладки программы.  
  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)  
 Содержит пошаговые инструкции по заданию DE, который вызывает операционной системы, чтобы запустить программу.  
  
 [Присоединение непосредственно к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Описывает процесс, используемый для отладки программы, в процессе, который уже выполняется.  
  
 [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Перечислены события, происходящие после присоединения DE в программу, пока программа не в его основную точку входа и готов для отладки.  
  
 [Элемент управления выполнения](../../extensibility/debugger/control-of-execution.md)  
 Объясняет, как DE обычно отправляет событие точки входа, событие завершения нагрузки или события остановки, в зависимости от обстоятельств.  
  
 [Связывание точек останова](../../extensibility/debugger/binding-breakpoints.md)  
 Описывает, как это сделать, если пользователь устанавливает точку останова, IDE формирует запрос и предлагает сеанса отладки, чтобы создать точку останова.  
  
 [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
 Объясняет, как создавать выражения и что происходит при вычислении выражения.  
  
 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Объясняет, как визуализаторами типов и пользовательских средств просмотра, поддерживаемых вычислитель выражений (EE).  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные принципы отладки архитектуры.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Общие компоненты отладки Visual Studio, которые включают DE, EE и обработчик символ (SH).  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как DE одновременно работает в пределах кода, документацию и контекстов выражения вычисления. Описание для каждого из трех контекстов, расположения, положение или оценки, относящиеся к нему.  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)