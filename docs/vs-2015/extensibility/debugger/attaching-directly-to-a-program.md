---
title: Подключение к программе | Документация Майкрософт
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
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de07b2fc8846bd24bb3e4483c78eb339d9d49e4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817552"
---
# <a name="attaching-directly-to-a-program"></a>Присоединение непосредственно к программе
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользователи, желающие Отладка программ в процессе, который обычно уже запущена, выполните следующие действия:  
  
1. В Интегрированной среде разработки выберите **отладить процессы** команду **средства** меню.  
  
    Откроется диалоговое окно **Процессы**.  
  
2. Выбор процесса и нажмите кнопку **Attach** кнопки.  
  
    **Присоединение к процессу** откроется диалоговое окно со списком всех отладчиков (DEs) установлен на компьютере.  
  
3. Укажите DEs, использовать выбранный процесс отладки, а затем нажмите кнопку **ОК**.  
  
   Размер пакета отладки начнет сеанс отладки и передает ему список DEs. Сеанс отладки в свою очередь передает этот список, а также функцию обратного вызова для выбранного процесса и затем запрашивает процесс перечислить его запущенных программ.  
  
   Программным образом в ответ на запрос пользователя, размер пакета отладки создает диспетчер отладки сеансов (SDM) и передает ему список выбранных DEs. Вместе со списком, размер пакета отладки передает SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) интерфейс. Размер пакета отладки передает список DEs для выбранного процесса путем вызова [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Затем вызывает SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) через порт для программ, работающих в процессе перечисления.  
  
   С этого момента каждого модуля отладки присоединяется к программе, точно так, как описано в [присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md), с двумя исключениями.  
  
   Для повышения эффективности DEs, которые реализуются для совместного использования адресное пространство с помощью SDM группируются таким образом, чтобы каждый DE имеет набор программ, которые он будет присоединен. В этом случае [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) вызовы [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) и передает его массив программ для присоединения к.  
  
   Второе исключение – то, что события запуска, отправленные DE, подключение к программе, на котором уже выполняется обычно не содержат точечное событие входа.  
  
## <a name="see-also"></a>См. также  
 [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)

