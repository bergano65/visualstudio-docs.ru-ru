---
title: Программы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 372cf5c64fde2009b8bddf8fa5800788ba0d6501
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970192"
---
# <a name="programs"></a>Programs
В архитектуре отладчик *программы*:  
  
-   — Это контейнер для набора потоков и набор модулей. Программа не имеет единый аналогов в операционной системе Windows.  
  
     Программа представляет собой подпроцесса. Например при отладке веб-сайта, сценарий можно рассматривать как программу. Во время запуска сценария в процессе написания сценария ядра, независимо от других сценариев, он также имеет свой собственный набор потоков. Отладчик (DE) присоединяет к программе, а не процесс или поток.  
  
-   Можно указать сам и процесс, в котором он выполняется в. Программы можно прикреплять к, следует отсоединить от и описывают DE, создавшего его, если таковые имеются. Программу можно также выполнить, остановить, продолжить и быть завершен.  
  
-   Можно перечислить все потоки. Программа также может предоставлять собственный поток Дизассемблированный код и можно перечислить все контексты кода для положения данного документа.  
  
-   Представленный [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, созданный до исполняемой программы или в ходе процесса присоединения в зависимости от реализации. При порт перечисляет программы процесса, каждая программа создается в соответствии с соответствующей [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, передается в качестве аргумента для [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Хотя отладчиков также создать `IDebugProgram2` интерфейсы для представления программы эти программы не создаются в соответствии с узлом программы. `IDebugProgramNode2` Интерфейсы, созданные DE используются для фактического отладки, то время как созданные порт используются только для обнаружения, какие программы работают в процессе.  
  
## <a name="see-also"></a>См. также  
 [Процессы](../../extensibility/debugger/processes.md)   
 [Узлы программы](../../extensibility/debugger/program-nodes.md)   
 [Модули](../../extensibility/debugger/modules.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Позиция в документе](../../extensibility/debugger/document-position.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)