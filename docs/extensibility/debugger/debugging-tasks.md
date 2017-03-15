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
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 08f6d64a86982ad7425a2e89815765ce63dbf28c
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-tasks"></a>Задачи отладки
Для отладки программы, необходимо запустить и отладчик (DE) должен быть подключен к нему, иначе DE должна быть присоединена к ранее запущенные программы. После присоединения, DE необходимо создавать определенные события запуска. В результате отладочный пакет пытается выполнить привязку точки останова, заданные в Интегрированной среде разработки. Когда программа достигает связанная точка останова, она останавливается и ждет ввод пользователя.  
  
## <a name="in-this-section"></a>Содержание  
 [Проблемы безопасности](../../extensibility/debugger/security-issues.md)  
 Описание действия безопасности, необходимые для отладки программы.  
  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)  
 Содержит пошаговые инструкции по заданию DE, который вызывает операционной системы, чтобы запустить программу.  
  
 [Подключение к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Описывает процесс, используемый для отладки программы, в процессе, который уже выполняется.  
  
 [Отправка события запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Перечислены события, происходящие после присоединения DE в программу, пока программа на основной точки входа и готов для отладки.  
  
 [Контроль выполнения](../../extensibility/debugger/control-of-execution.md)  
 Объясняет, как DE обычно отправляет события точки входа, событие завершения загрузки или событии остановки, в зависимости от обстоятельств.  
  
 [Привязка точки останова](../../extensibility/debugger/binding-breakpoints.md)  
 Описывается, если пользователь устанавливает точку останова, IDE формирует запрос и запрашивает сеанса отладки, чтобы создать точки останова.  
  
 [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
 Объясняет, как создавать выражения и что происходит при вычислении выражения.  
  
 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Объясняет, как тип визуализаторы и пользовательские средства просмотра поддерживаются средством оценки выражений (EE).  
  
## <a name="related-sections"></a>Связанные разделы  
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Общие компоненты отладки Visual Studio, включая DE, EE и обработчик символ (SH).  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняет, как DE одновременно работает внутри кода, документацию и контекстов выражения вычислений. Описание для каждого из трех контекстов, расположение, положение или оценки, относящиеся к нему.  
  
## <a name="see-also"></a>См. также  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
