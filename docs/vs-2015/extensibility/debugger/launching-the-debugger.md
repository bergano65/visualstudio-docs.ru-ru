---
title: Запуск отладчика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2a427825fdc10811fccc10ddc71438b406ebd5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559253"
---
# <a name="launching-the-debugger"></a>Запуск отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [запуск отладчика](https://docs.microsoft.com/visualstudio/extensibility/debugger/launching-the-debugger).  
  
Запуск отладчика требуется отправить правильную последовательность методов и событий с использованием их соответствующие атрибуты.  
  
## <a name="sequences-of-methods-and-events"></a>Последовательности методы и события  
  
1.  Диспетчер отладки сеансов (SDM) называется, выбрав **Отладка** меню, а затем выбрать **запустить**. См. в разделе [запуск программы](../../extensibility/debugger/launching-a-program.md) Дополнительные сведения.  
  
2.  Вызовы SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  
  
3.  На основе модели процесса отладки ядра (DE), `IDebugProgramNodeAttach2::OnAttach` метод возвращает одно из следующих методов, которые определяет, что будет дальше.  
  
     Если `S_FALSE` возвращается, модуль отладки (DE), будет необходимо загрузить процессе виртуальной машины.  
  
     - или -  
  
     Если `S_OK` возвращается, DE является необходимо загрузить в процессе из SDM. SDM выполняет следующие задачи:  
  
    1.  Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) получить сведения из DE.  
  
    2.  Совместно создает DE.  
  
    3.  Вызовы [присоединить](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Отправляет DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
5.  Отправляет DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
6.  Отправляет DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
7.  Отправляет DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
8.  Отправляет DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)   
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)

