---
title: Присоединение и отсоединение программы | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6915d54dca921f9600a51c3501ed9a4808bca199
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288708"
---
# <a name="attaching-and-detaching-to-a-program"></a>Присоединение к программе и отсоединение от нее
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подключение отладчика требуется отправить правильную последовательность методов и событий с верными атрибутами.  
  
## <a name="sequence-of-methods-and-events"></a>Последовательность методов и событий  
  
1.  Диспетчер отладки сеансов (SDM) вызывает [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод.  
  
     На основе модели процесса отладки ядра (DE), `IDebugProgramNodeAttach2::OnAttach` метод возвращает одно из следующих методов, которые определяет, что будет дальше.  
  
     Если `S_FALSE` возвращается, модуль отладки успешного присоединения к программе. В противном случае [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод вызывается для завершения процесса присоединения.  
  
     Если `S_OK` возвращается, DE является должен быть загружен в тот же процесс, что SDM. SDM выполняет следующие задачи:  
  
    1.  Вызовы [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) получить сведения из DE.  
  
    2.  Совместно создает DE.  
  
    3.  Вызовы [присоединить](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Отправляет DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
3.  Отправляет DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) для SDM с `EVENT_SYNC` атрибута.  
  
4.  Отправляет DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) для SDM с `EVENT_SYNC_STOP` атрибута.  
  
 Отсоединение от программы является простое, двухэтапный процесс, следующим образом:  
  
1.  Вызовы SDM [отсоединения](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Отправляет DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)

