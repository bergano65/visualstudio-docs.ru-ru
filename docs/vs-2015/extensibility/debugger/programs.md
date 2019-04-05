---
title: Программы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c9beccd5e72c26d695d443c4ab2aa4198e71784
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994282"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
