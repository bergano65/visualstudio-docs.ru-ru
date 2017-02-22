---
title: "Отладка пакета | Microsoft Docs"
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
  - "отладка [пакет SDK для отладки], пакеты"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Отладка пакета
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пакет отладки работает в оболочке Visual Studio и обрабатывает все пользовательский интерфейс.  Он использует интерфейсы отладки Visual Studio и связывается с сеансом \(SDM\) диспетчер отладки.  
  
 Разбейте события, передаваемые через параметр SDM отладчик из режима выполнения в режим приостановки и изменение фокуса в программе, в котором прерывание.  Пакет отладки отслеживает кадр стека, и поток из информации, отправленного в него событиями.  
  
 Пакет отладки нет зависимостей языка или среды выполнения.  Нет необходимости реализовывать или изменить пакеты отладки.  
  
 Пакет отладки реализуется vsdebug.dll.  
  
## См. также  
 [Диспетчер сеансов отладки](../../extensibility/debugger/session-debug-manager.md)   
 [Кадры стека](../../extensibility/debugger/stack-frames.md)   
 [Потоки](../../extensibility/debugger/threads.md)   
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)