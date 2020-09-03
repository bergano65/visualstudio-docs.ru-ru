---
title: Прямое подключение к программе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147997"
---
# <a name="attaching-directly-to-a-program"></a>Присоединение непосредственно к программе
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользователи, которые хотят отлаживать программы в уже запущенном процессе, обычно следуют этому процессу:  
  
1. В интегрированной среде разработки выберите команду **Отладка процессов** в меню **Сервис** .  
  
    Откроется диалоговое окно **Процессы**.  
  
2. Выберите процесс и нажмите кнопку **присоединить** .  
  
    Откроется диалоговое окно **Присоединение к процессу** , в котором перечислены все модули отладки (DEs), установленные на компьютере.  
  
3. Укажите алгоритм DEs, который будет использоваться для отладки выбранного процесса, и нажмите кнопку **ОК**.  
  
   Пакет отладки запускает сеанс отладки и передает ему список DEs. Сеанс отладки, в свою очередь, передает этот список вместе с функцией обратного вызова в выбранный процесс, а затем запрашивает в процессе перечисление выполняющихся программ.  
  
   Программно, в ответ на запрос пользователя, пакет отладки создает экземпляр диспетчера отладки сеанса и передает ему список выбранного DEs. Вместе со списком пакет отладки передает SDM интерфейс [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Пакет отладки передает список DEs в выбранный процесс путем вызова [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Затем SDM вызывает [IDebugProcess2:: енумпрограмс](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) в порте для перечисления программ, выполняющихся в процессе.  
  
   С этого момента каждый модуль отладки прикрепляется к программе точно так же, как описано в подсоединении [после запуска](../../extensibility/debugger/attaching-after-a-launch.md), с двумя исключениями.  
  
   Для повышения эффективности алгоритмы DEs, реализованные для совместного использования адресного пространства с SDM, группируются так, чтобы каждый из них получил набор программ, к которым он будет присоединен. В этом случае [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) вызывает [IDebugEngine2:: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) и передает ему массив программ для присоединения к.  
  
   Второе исключение заключается в том, что события запуска, отправленные с помощью DE-подключения к уже запущенной программе, обычно не включают в себя событие точки входа.  
  
## <a name="see-also"></a>См. также:  
 [Отправка событий запуска после запуска](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
