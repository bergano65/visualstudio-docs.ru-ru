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
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153643"
---
# <a name="programs"></a>Программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика **Программа**:  
  
- — Это контейнер для набора потоков и набора модулей. Программа не имеет единого аналога в операционной системе Windows.  
  
     Программа — это разновидность подпроцесса. Например, при отладке веб-сайта сценарий может рассматриваться как программа. Хотя скрипт выполняется в процессе обработчика скриптов, независимо от других скриптов, он также имеет собственный набор потоков. Модуль отладки (DE) подключается к программе, а не к процессу или потоку.  
  
- Может идентифицировать себя и процесс, в котором он выполняется, и может быть присоединен к, отсоединяться от, а также описывать DE, который создал его, если таковой имеется. Программа может выполнять, останавливаться, продолжать работу и завершаться.  
  
- Может перечислить все его потоки. Программа может также предоставить собственный поток дизассемблирования и перечислить все контексты кода заданной позицией документа.  
  
- Представляется интерфейсом [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , созданным перед присоединением программы или в рамках процесса присоединения в зависимости от реализации. Когда порт перечисляет программы процесса, каждая программа создается в соответствии с соответствующим интерфейсом [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , переданным в качестве аргумента в [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Хотя модули отладки также создают `IDebugProgram2` интерфейсы для представления программ, эти программы не создаются в соответствии с узлом программы. `IDebugProgramNode2`Интерфейсы, созданные методом de, используются для фактической отладки, а созданные портом используются только для обнаружения выполняющихся в процессе программ.  
  
## <a name="see-also"></a>См. также:  
 [Операций](../../extensibility/debugger/processes.md)   
 [Узлы программы](../../extensibility/debugger/program-nodes.md)   
 [Модуле](../../extensibility/debugger/modules.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [Расположение документа](../../extensibility/debugger/document-position.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
