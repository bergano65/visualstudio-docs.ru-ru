---
title: Пошаговое выполнение в режиме приостановки выполнения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423365"
---
# <a name="stepping-in-break-mode"></a>Пошаговое выполнение в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, выполняемый, когда отладчик находится в режиме приостановки выполнения и должен проходить код по шагам:  
  
## <a name="stepping-process"></a>Процесс пошагового выполнения  
  
1. Вызовите [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с аргументами [степкинд](../../extensibility/debugger/reference/stepkind.md) и [степунит](../../extensibility/debugger/reference/stepunit.md) , чтобы выполнить шаг.  
  
2. По завершении действия отправьте [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
