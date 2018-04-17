---
title: На основе запуска вложение | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 892518cc92286f9415e39c96b6ed2afa8eb0d792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="launch-based-attachment"></a>На основе запуска вложения
На основе запуска вложения к программе выполняется автоматически. При запуске процесса, размещающего программа SDM, вложения на основе запуска следует путь, подобный метод вручную вложения. Сведения см. в разделе [присоединение к программе](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Присоединение процесса  
 Основное отличие заключается в последовательность событий после **присоединение** вызвать, как показано ниже:  
  
1.  Отправить **IDebugEngineCreateEvent2** SDM объекта события. Дополнительные сведения см. в разделе [отправки событий](../../extensibility/debugger/sending-events.md).  
  
2.  Вызовите `IDebugProgram2::GetProgramId` метод **IDebugProgram2** передается интерфейс **присоединение** метод.  
  
3.  Отправить **IDebugProgramCreateEvent2** объект события для уведомления SDM, локальной **IDebugProgram2** был создан объект, представляющий программу DE.  
  
4.  Отправить [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) объект события для уведомления SDM, для процесса, который запускается, создается новый поток.  
  
## <a name="see-also"></a>См. также  
 [Отправка необходимых событий](../../extensibility/debugger/sending-the-required-events.md)   
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)