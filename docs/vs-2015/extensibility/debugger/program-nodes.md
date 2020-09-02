---
title: Узлы программы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153648"
---
# <a name="program-nodes"></a>Узлы программы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика — **узел программы**:  
  
- — Это упрощенное описание программы.  
  
- Может идентифицировать себя и процесс, в котором он выполняется, и может быть присоединен к, отсоединяться от и описывать подсистему отладки (DE), в которой он был создан, если таковой имеется.  
  
- Представляется интерфейсом [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , который обычно создается методом de или Port. Узлы программы добавляются в порт путем вызова [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). При добавлении к порту узла программы он добавляется в процесс, содержащий программу, которую представляет этот узел программы.  
  
  Иногда после запуска сеанса отладки, в зависимости от реализации пакета отладки, узлы программы используются для создания соответствующих программ. Когда процесс запрашивается для своих программ, выполняется перечисление программ, по одному для каждого узла программы.  
  
  Перед присоединением программы к среде IDE требуется только упрощенное описание программы. Эти сведения можно получить из узла программы. После того как программа подключена к, интегрированная среда разработки должна отобразить более подробную информацию, например список всех потоков, выполняющихся в программе. Эти сведения получаются из самой программы.  
  
## <a name="see-also"></a>См. также:  
 [Приложениями](../../extensibility/debugger/programs.md)   
 [Операций](../../extensibility/debugger/processes.md)   
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
