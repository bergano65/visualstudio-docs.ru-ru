---
title: Присоединение к программе | Документация Майкрософт
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
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9beb92c67e196f76d8a59559825a844f0e0c8a7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849025"
---
# <a name="attaching-to-the-program"></a>Присоединение к программе
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После регистрации ваших программ с соответствующий порт, необходимо подключить отладчик к программу, которую требуется отладить.  
  
## <a name="choosing-how-to-attach"></a>Выбрав способ прикрепления  
 Существует три способа, в которых диспетчер отладки сеансов (SDM) пытается присоединиться к отлаживаемой программы.  
  
1. Для программ, которые запускаются ядром отладки через [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (что типично для интерпретируемых языков, например), SDM получает [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс из [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с программой, присоединяемый к. Если можно получить SDM `IDebugProgramNodeAttach2` SDM интерфейс, затем вызывает [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод. `IDebugProgramNodeAttach2::OnAttach` Возвращает метод `S_OK` чтобы указать, что он не вложен в программу, и что другие попытки могут выполняться для присоединения к программе.  
  
2. Если можно получить SDM [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) интерфейс из программы, присоединяемый к вызовы SDM [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) метод. Этот подход является типичным для программ, которые были удаленно запускать с поставщика порта.  
  
3. Если программа не может быть присоединена через `IDebugProgramNodeAttach2::OnAttach` или `IDebugProgramEx2::Attach` методы, SDM загружает модуль отладки (если еще не загружен) путем вызова `CoCreateInstance` функции, а затем вызывает [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод. Этот подход является типичным для программ, запускать локально поставщика порта.  
  
    Можно также для поставщика пользовательского порта для вызова `IDebugEngine2::Attach` метод в реализации поставщика пользовательского порта `IDebugProgramEx2::Attach` метод. В этом случае обычно поставщика пользовательского порта запускает модуль отладки на удаленном компьютере.  
  
   Вложение достигается, когда диспетчер отладки сеансов (SDM) вызывает [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
   Если вы запустите вашей DE в том же процессе, что и приложение для отладки, а затем необходимо реализовать следующие методы класса [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  После `IDebugEngine2::Attach` вызывается метод, выполните следующие действия в своей реализации `IDebugEngine2::Attach` метод:  
  
1.  Отправить [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) объект события для SDM. Дополнительные сведения см. в разделе [отправки событий](../../extensibility/debugger/sending-events.md).  
  
2.  Вызовите [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, который был передан `IDebugEngine2::Attach` метод.  
  
     Эта команда возвращает `GUID` , используемый для идентификации программы. `GUID` Должны храниться в объекте представляет локальной программу DE, что он должен быть возвращен при `IDebugProgram2::GetProgramId` вызывается метод `IDebugProgram2` интерфейс.  
  
    > [!NOTE]
    >  Если вы реализуете `IDebugProgramNodeAttach2` интерфейс программы `GUID` передается `IDebugProgramNodeAttach2::OnAttach` метод. Это `GUID` используется для программы `GUID` возвращаемые `IDebugProgram2::GetProgramId` метод.  
  
3.  Отправить [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) объект события для уведомления SDM, локальной `IDebugProgram2` объект был создан для представления программы для DE. Дополнительные сведения см. в разделе [отправки событий](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Это не то же самое `IDebugProgram2` объект, который был передан в `IDebugEngine2::Attach` метод. Ранее переданный `IDebugProgram2` объект распознается только номер порта и представляет собой отдельный объект.  
  
## <a name="see-also"></a>См. также  
 [Вложение на основе запуска](../../extensibility/debugger/launch-based-attachment.md)   
 [Отправка событий](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Присоединение](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

