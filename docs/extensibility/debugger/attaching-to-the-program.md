---
title: Присоединение к программе | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c9719f6258f3bbb5cc8323693001c7f1a9d47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107872"
---
# <a name="attaching-to-the-program"></a>Присоединение к программе
После регистрации программах с соответствующим портом, необходимо подключить отладчик для программы, которую требуется отладить.  
  
## <a name="choosing-how-to-attach"></a>Выбор способа присоединения  
 Существует три способа, в которых Диспетчер сеанса отладки (SDM) пытается присоединиться к отлаживаемой программы.  
  
1.  Для программ, которые загружаются модуль отладки с помощью [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (что типично для интерпретируемых языки, например), SDM получает [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейс из [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с программой, присоединяемый к. Если можно получить SDM `IDebugProgramNodeAttach2` SDM интерфейса, затем вызывает [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод. `IDebugProgramNodeAttach2::OnAttach` Возвращает `S_OK` чтобы указать, что он не вложен в программу и предоставления других попыток для присоединения к программе.  
  
2.  Если можно получить SDM [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) интерфейс из программы, присоединяемый к вызовы SDM [присоединение](../../extensibility/debugger/reference/idebugprogramex2-attach.md) метод. Этот подход является типичным для программ, которое было запущенно удаленно поставщика порта.  
  
3.  Если программа не может быть присоединена через `IDebugProgramNodeAttach2::OnAttach` или `IDebugProgramEx2::Attach` методы, SDM загружает модуль отладки (если еще не загружен) путем вызова `CoCreateInstance` функции, а затем вызывает метод [присоединение](../../extensibility/debugger/reference/idebugengine2-attach.md) метод. Этот подход является типичным для программ, запускать локально поставщика порта.  
  
     Можно также для других поставщиков другой номер порта для вызова `IDebugEngine2::Attach` метод в реализации поставщика пользовательских порта `IDebugProgramEx2::Attach` метод. Обычно в этом случае поставщик пользовательский порт запускает модуль отладки на удаленном компьютере.  
  
 Вложение достигается, когда диспетчер сеанса отладки (SDM) вызывает [присоединение](../../extensibility/debugger/reference/idebugengine2-attach.md) метод.  
  
 Если запустить ваш DE в том же процессе, что и приложение для отладки, то необходимо реализовать следующие методы [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 После `IDebugEngine2::Attach` вызывается метод, выполните следующие действия в реализации `IDebugEngine2::Attach` метод:  
  
1.  Отправить [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM объекта события. Дополнительные сведения см. в разделе [отправки событий](../../extensibility/debugger/sending-events.md).  
  
2.  Вызовите [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, который был передан в `IDebugEngine2::Attach` метод.  
  
     Возвращает `GUID` , используемый для идентификации программы. `GUID` Должны храниться в объекте представляет локальный программировать DE, что он должен быть возвращен при `IDebugProgram2::GetProgramId` метод будет вызван на `IDebugProgram2` интерфейса.  
  
    > [!NOTE]
    >  Если вы реализуете `IDebugProgramNodeAttach2` интерфейс программы `GUID` передается `IDebugProgramNodeAttach2::OnAttach` метод. Это `GUID` используется для программы `GUID` возвращенных `IDebugProgram2::GetProgramId` метод.  
  
3.  Отправить [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) объект события для уведомления SDM, локальной `IDebugProgram2` был создан объект, представляющий программу DE. Дополнительные сведения см. в разделе [отправки событий](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Это не то же самое `IDebugProgram2` объекта, переданного в `IDebugEngine2::Attach` метод. Ранее переданный `IDebugProgram2` объект распознается только порт и представляет собой отдельный объект.  
  
## <a name="see-also"></a>См. также  
 [На основе запуска вложения](../../extensibility/debugger/launch-based-attachment.md)   
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