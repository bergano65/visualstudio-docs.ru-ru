---
title: Уведомление порта | Документация Майкрософт
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
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4faaea47196e6d247aa62c5a9d067970ddeaaec4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937075"
---
# <a name="notifying-the-port"></a>Уведомление порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После запуска программы, порт должен быть уведомлен, следующим образом:  
  
1. Порт, получив новый узел программы, он отправляет событие создания сеанса отладки. Событие несет с собой интерфейс, который представляет программу.  
  
2. Сеанс отладки запрашивает программа для идентификатора модуля отладки (DE), которое можно присоединить к.  
  
3. Сеанс отладки проверяет, находится ли DE включен в список допустимых DEs для этой программы. Сеанс отладки получает этот список из параметров активную программу решения, изначально переданные ему размер пакета отладки.  
  
    DE должны находиться в список допустимых, иначе DE не будет присоединен к программе.  
  
   Программным образом, когда порт сначала получает новый узел программы, он создает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для представления программы.  
  
> [!NOTE]
>  Это не следует путать с `IDebugProgram2` интерфейса, созданного в более поздней версии ядром отладки (DE).  
  
 Отправляет порт [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) события создания программы диспетчеру сеанса отладки (SDM) с помощью COM `IConnectionPoint` интерфейс.  
  
> [!NOTE]
>  Это не следует путать с `IDebugProgramCreateEvent2` интерфейс, который отправляется DE позже.  
  
 А также сам интерфейс событий, отправляет порт [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), и [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейсы, которые представляют порт, обрабатывать, и Программа, соответственно. Вызовы SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) для получения идентификатора GUID DE, который можно отлаживать программы. Идентификатор GUID, первоначально полученную из [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс.  
  
 SDM проверяет, находится ли DE включен в список допустимых DEs. SDM получает этот список из параметров активную программу решения, изначально переданные ему размер пакета отладки. DE должны находиться в список допустимых, иначе он не будет присоединен к программе.  
  
 После получения удостоверения DE SDM готовы присоединить ее к программе.  
  
## <a name="see-also"></a>См. также  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)   
 [Присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)

