---
title: Программа узлов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41ce3fd47850df5bab1db771177637102e9ec57a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287889"
---
# <a name="program-nodes"></a>Узлы программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

С точки зрения архитектуры отладчика **узел программы**:  
  
-   — Это упрощенный описание программы.  
  
-   Можно указать сам и процесс его выполнение и может быть присоединен, следует отсоединить от и описать отладчик (DE), были созданы, если таковые имеются.  
  
-   Представленный [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, обычно создается с DE или порт. Программа узлы добавляются к порту, вызвав [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). При программы узел добавляется к порту, она добавляется к процессу с программой, которую представляет данный узел программы.  
  
 Через некоторое время после запуска сеанса отладки, в зависимости от реализации пакета отладки, узлы программы используются для создания соответствующих программ. При запросе к процесса для своих программ, перечислены программы, один для каждого узла программы.  
  
 Программа будет подключен к, интегрированной среды разработки должна упрощенных описание программы. Эти сведения можно получить из узла программы. Присоединенная программы для интегрированной среды разработки необходимо получить более подробные сведения, такие как список всех потоков в программе. Эта информация получается из самой программы.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Процессы](../../extensibility/debugger/processes.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

