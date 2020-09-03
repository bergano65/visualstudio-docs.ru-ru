---
title: Задачи отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4a8a9879bce6d91448bb4f29b842328ab56bb97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200608"
---
# <a name="debugging-tasks"></a>Задачи отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы выполнить отладку программы, она должна быть запущена и к ней должен быть присоединен отладчик (DE), или же DE должен быть присоединен к ранее запущенной программе. После присоединения DE должен создать определенные события запуска. В ответ пакет отладки пытается привязать точки останова, заданные в интегрированной среде разработки. Когда программа достигает привязанной точки останова, она останавливается и ожидает ввода данных пользователем.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Проблемы с безопасностью](../../extensibility/debugger/security-issues.md)  
 Описание действий по обеспечению безопасности, необходимых для отладки программы.  
  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)  
 Содержит пошаговые инструкции по заданию DE, который вызывает операционную систему для запуска программы.  
  
 [Присоединение непосредственно к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Описывает процесс, используемый для отладки программы в уже запущенном процессе.  
  
 [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Список событий, происходящих после присоединения к программе, до тех пор, пока программа не станет основной точкой входа и не будет готова к отладке.  
  
 [Элемент управления выполнения](../../extensibility/debugger/control-of-execution.md)  
 Объясняет, как в методе DE обычно отправляется событие точки входа, событие загрузки или событие остановки, в зависимости от обстоятельств.  
  
 [Связывание точек останова](../../extensibility/debugger/binding-breakpoints.md)  
 Описывает, как, если пользователь устанавливает точку останова, интегрированная среда разработки формирует запрос и запрашивает у сеанса отладки создание точки останова.  
  
 [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)  
 Объясняет, как создаются выражения и что происходит при вычислении выражения.  
  
 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Описывает, как визуализаторы типов и пользовательские средства просмотра поддерживаются средством оценки выражений (EE).  
  
## <a name="related-sections"></a>См. также  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные понятия архитектуры отладки.  
  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)  
 Содержит общие сведения о компонентах отладки Visual Studio, включая DE, EE и обработчик символов (SH).  
  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)  
 Объясняется, как происходит одновременное отключение в рамках кода, документации и контекстов оценки выражений. Описывает, для каждого из трех контекстов: расположение, положение или вычисление, относящиеся к нему.  
  
## <a name="see-also"></a>См. также:  
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
