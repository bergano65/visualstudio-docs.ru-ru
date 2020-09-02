---
title: Процессы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153670"
---
# <a name="processes"></a>Процессы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика **процесс**:  
  
- — Это контейнер для набора программ. Он тесно аналогичен процессу Windows, который является контейнером для набора потоков.  
  
- Может идентифицировать себя по имени, идентификатору или физическому идентификатору.  
  
- Может перечислить все выполняющиеся программы (и их потоки).  
  
- Может описывать себя, порт, в котором он выполняется, и компьютер, на котором он находится.  
  
- Может создать одну или несколько программ, завершить любую из создаваемых программ или вызвать прекращение работы программы.  
  
- Представляется интерфейсом [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , который создается при запуске процесса. Процесс запускается либо диспетчером отладки сеансов (SDM), либо [лаунчсуспендед](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  Пакет отладки может подключить к процессу модуль отладки (DE), вызвав [attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Это означает, что компонент DE подключается ко всем возможным программам, выполняемым в процессе, который он может обработать. Например, если среда CLR отключится к процессу, она будет присоединена только к программам, выполняющим управляемый код.  
  
## <a name="see-also"></a>См. также:  
 [Приложениями](../../extensibility/debugger/programs.md)   
 [Многопоточно](../../extensibility/debugger/threads.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Пакет отладки](../../extensibility/debugger/debug-package.md)   
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [лаунчсуспендед](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
