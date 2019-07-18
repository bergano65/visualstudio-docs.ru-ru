---
title: Завершение и отсоединение | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176669"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается нормальное завершение.  
  
## <a name="discussion"></a>Обсуждение  
 После [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) интерфейса продолжается, если отсутствуют точки останова, исключения, ошибки времени выполнения или бесконечных циклов в приложении для отладки, Отлаживаемая программа будет выполняться до завершения. Это нормальное завершение.  
  
 Необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) для реализации нормальное завершение. Это требует внедрения [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) метод.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
