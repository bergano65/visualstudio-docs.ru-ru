---
title: Шаг с заходом в режиме приостановки выполнения | Документация Майкрософт
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
ms.openlocfilehash: e185727343cc7b6be144583c22f78b607af2eec0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994374"
---
# <a name="stepping-in-break-mode"></a>Пошаговое выполнение в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и необходимо пошаговое выполнение кода:  
  
## <a name="stepping-process"></a>Пошаговое выполнение процесса  
  
1.  Вызовите [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с [STEPKIND](../../extensibility/debugger/reference/stepkind.md) и [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) аргументы для выполнения шага.  
  
2.  По завершении шага отправки [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
