---
title: "Запуск отладчика | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23fd772b74c4caafbde37541933c38e306f9dc75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="launching-the-debugger"></a>Запуск отладчика
Запуск отладчика требуется отправить правильной последовательности, методов и событий с их соответствующие атрибуты.  
  
## <a name="sequences-of-methods-and-events"></a>Последовательности, методов и событий  
  
1.  Диспетчер сеансов отладки (SDM) называется, выбрав **отладки** меню, а затем выберите **запустить**. В разделе [запустив программу](../../extensibility/debugger/launching-a-program.md) для получения дополнительной информации.  
  
2.  Вызовы SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  
  
3.  На основе модели процесса отладки ядра (DE), `IDebugProgramNodeAttach2::OnAttach` метод возвращает одно из следующих методов, которые определяет дальнейший ход событий.  
  
     Если `S_FALSE` возвращается, ядро отладки (DE) — для загрузки процессе виртуальной машины.  
  
     -или-  
  
     Если `S_OK` возвращается, DE является для загрузки в процессе из SDM. Затем SDM выполняет следующие задачи:  
  
    1.  Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) для получения информация DE для поисковых систем.  
  
    2.  Совместно создает DE.  
  
    3.  Вызовы [присоединения](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Отправляет DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
5.  Отправляет DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
6.  Отправляет DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
7.  Отправляет DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
8.  Отправляет DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
## <a name="see-also"></a>См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)   
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)