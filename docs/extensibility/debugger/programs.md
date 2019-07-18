---
title: Программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e70a970aad250a30e19fd27ac3a47732952b3bf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351397"
---
# <a name="programs"></a>Programs
В архитектуре отладчик *программы*:

- — Это контейнер для набора потоков и набор модулей. Программа не имеет единый аналогов в операционной системе Windows.

     Программа представляет собой подпроцесса. Например при отладке веб-сайта, сценарий можно рассматривать как программу. Во время запуска сценария в процессе написания сценария ядра, независимо от других сценариев, он также имеет свой собственный набор потоков. Отладчик (DE) присоединяет к программе, а не процесс или поток.

- Можно указать сам и процесс, в котором он выполняется в. Программы можно прикреплять к, следует отсоединить от и описывают DE, создавшего его, если таковые имеются. Программу можно также выполнить, остановить, продолжить и быть завершен.

- Можно перечислить все потоки. Программа также может предоставлять собственный поток Дизассемблированный код и можно перечислить все контексты кода для положения данного документа.

- Представленный [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, созданный до исполняемой программы или в ходе процесса присоединения в зависимости от реализации. При порт перечисляет программы процесса, каждая программа создается в соответствии с соответствующей [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, передается в качестве аргумента для [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Хотя отладчиков также создать `IDebugProgram2` интерфейсы для представления программы эти программы не создаются в соответствии с узлом программы. `IDebugProgramNode2` Интерфейсы, созданные DE используются для фактического отладки, то время как созданные порт используются только для обнаружения, какие программы работают в процессе.

## <a name="see-also"></a>См. также
- [Процессы](../../extensibility/debugger/processes.md)
- [Узлы программы](../../extensibility/debugger/program-nodes.md)
- [Модули](../../extensibility/debugger/modules.md)
- [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)
- [Отладка ядра](../../extensibility/debugger/debug-engine.md)
- [Позиция в документе](../../extensibility/debugger/document-position.md)
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)