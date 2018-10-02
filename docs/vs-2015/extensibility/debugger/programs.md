---
title: Программы | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c6db9d45f9bb421738b71e630482cbbb8f6525c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573273"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [программы](https://docs.microsoft.com/visualstudio/extensibility/debugger/programs).  
  
С точки зрения архитектуры отладчика **программы**:  
  
-   — Это контейнер для набора потоков и набор модулей. Программа не имеет единый аналогов в операционной системе Windows.  
  
     Программа представляет собой подпроцесса. Например при отладке веб-сайта, сценарий можно рассматривать как программу. Во время запуска сценария в процессе написания сценария ядра, независимо от других сценариев, он также имеет свой собственный набор потоков. Отладчик (DE) присоединяет к программе, а не процесс или поток.  
  
-   Можно указать сам и процесс его выполнение и может быть присоединен, следует отсоединить от и описать DE, создавшего его, если таковые имеются. Программа может выполнить, остановить, продолжить и быть прервана.  
  
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

