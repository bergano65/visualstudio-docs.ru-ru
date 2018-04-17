---
title: Завершение и отсоединения | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5af218098f6d79cf6208c66b314c35d2471af15
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
Далее описывается нормального завершения.  
  
## <a name="discussion"></a>Обсуждение  
 После [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) интерфейс продолжается, если отсутствуют точки останова, исключения, ошибки во время выполнения или бесконечные циклы в приложении для отладки, Отлаживаемая программа будет выполняться до завершения. Это нормальное завершение.  
  
 Вы должны отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) для реализации нормального завершения. Это требует внедрения [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)