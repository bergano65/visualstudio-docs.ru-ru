---
title: "На основе запуска вложения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладчики, запуск"
  - "отладчики, присоединение к программам"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# На основе запуска вложения
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Запуск\-основанное автоматическое вложение в программе.  При запуске процесса размещения программы SDM, запуск\-основанное вложения выполните, аналогично параметрам ручного метода вложения.  Дополнительные сведения см. в разделе [Вложение в программе](../../extensibility/debugger/attaching-to-the-program.md).  
  
## Вложа процесс  
 Основное различие последовательность событий, за которым следует **Присоединиться** вызов следующим образом:  
  
1.  Send IDebugEngineCreateEvent2 объект события в SDM.  Дополнительные сведения см. в разделе [Отправлять события](../../extensibility/debugger/sending-events.md).  
  
2.  Вызовите `IDebugProgram2::GetProgramId` метод  **IDebugProgram2** интерфейс, передаваемый  **Присоединиться** метод.  
  
3.  Send **IDebugProgramCreateEvent2** объект события для оповещения SDM, локальное  **IDebugProgram2** объект создан для представления программы с DE.  
  
4.  Send IDebugThreadCreateEvent2 объект события для оповещения SDM, что новый создания потока для процесса, запустившего.  
  
## См. также  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)