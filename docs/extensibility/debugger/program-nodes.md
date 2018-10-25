---
title: Программа узлов | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc87a24b35993f200c709ee033fffe6a4ecb120
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903625"
---
# <a name="program-nodes"></a>Узлы программы
В архитектуре отладчик *узел программы*:  
  
- — Это упрощенный описание программы.  
  
- Можно указать сам и процесс, в котором он выполняется в. Узел программы можно прикреплять к, следует отсоединить от и описывают отладчик (DE), были созданы, если таковые имеются.  
  
- Представленный [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, обычно создается с DE или порт. Программа узлы добавляются к порту, вызвав [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). При программы узел добавляется к порту, она добавляется к процессу с программой, которую представляет данный узел программы.  
  
  Через некоторое время после запуска сеанса отладки, в зависимости от реализации пакета отладки, узлы программы используются для создания соответствующих программ. При запросе к процесса для своих программ, перечислены программы, один для каждого узла программы.  
  
  Программа будет подключен к, интегрированной среды разработки должна упрощенных описание программы. Эти сведения можно получить из узла программы. Когда программа будет подключен к, интегрированная среда разработки отображает более подробные сведения, такие как список всех потоков в программе. Эта информация получается из самой программы.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Процессы](../../extensibility/debugger/processes.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)