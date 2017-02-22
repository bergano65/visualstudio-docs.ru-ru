---
title: "Завершение и отсоединения | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "программы, событий завершения"
  - "отладчики, отсоединение от программы"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Завершение и отсоединения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается нормальное завершение.  
  
## Обсуждение  
 После [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) OR  [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) интерфейс продолжается, если отсутствуют точки останова, исключения ошибки во время выполнения или бесконечные циклы в приложении быть отлаживанным, то, отлаживанными программа выполняется до завершения.  Это обычное завершение.  
  
 Необходимо отправлять IDebugProgramDestroyEvent2 к прекращению обычного ".  Это требует реализации [IDebugProgramDestroyEvent2:: GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md) метод.  
  
## См. также  
 [Создание пользовательские отладки ядра](../../extensibility/debugger/creating-a-custom-debug-engine.md)