---
title: "Программы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
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
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programs
С точки зрения архитектуры отладчика **программы**:  
  
-   Представляет контейнер для набор потоков и набор модулей. Программа не имеет один аналогов в операционной системе Windows.  
  
     Программа представляет собой подпроцесса. Например при отладке веб-сайта сценария можно рассматривать как программы. Во время выполнения сценария в процессе обработчик сценариев, независимо от других сценариев, он также имеет свой собственный набор потоков. Подсистема отладки (DE) присоединяет к программе, а не процесс или поток.  
  
-   Можно определить самостоятельно и процесс выполняется в он может быть присоединен, отсоединяется от и описать DE, создавший его, если таковые имеются. Программа может выполнить, остановить, продолжить и быть прервана.  
  
-   Можно перечислить все потоки. Программу можно также указать собственный поток Дизассемблированный код и можно перечислить все контексты кода положения данного документа.  
  
-   Представлена [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейс, созданный до исполняемой программы или как часть процесса подключения, в зависимости от реализации. Создается при порт перечислены программы, процесса, каждой программы в соответствии с соответствующей [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) в качестве аргумента передается интерфейс [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). А также создавать отладчики `IDebugProgram2` интерфейсы для представления программы, эти программы не создаются в соответствии с узлом программы. `IDebugProgramNode2` Интерфейсы, созданные DE используются для фактического отладки созданные порта используются только для определения, какие программы работают в процессе.  
  
## <a name="see-also"></a>См. также  
 [Процессы](../../extensibility/debugger/processes.md)   
 [Программа узлов](../../extensibility/debugger/program-nodes.md)   
 [Модули](../../extensibility/debugger/modules.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Позиция в документе](../../extensibility/debugger/document-position.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
