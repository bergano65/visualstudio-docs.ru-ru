---
title: Присоединение к Программе (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739244"
---
# <a name="attach-to-the-program"></a>Прикрепите к программе
После регистрации программ в соответствующем порту необходимо прикрепить отладчикки к программе, которая требуетотого отладки.

## <a name="choose-how-to-attach"></a>Выберите, как прикрепить
 Существует три способа, с которыми диспетчер сеанса отладки (SDM) пытается прикрепить к отладке программы.

1. Для программ, запускаемых отладкой через метод [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (типичный для интерпретированных языков, например), SDM получает интерфейс [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) от объекта [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) связанного с прилагаемым к программе. Если SDM может `IDebugProgramNodeAttach2` получить интерфейс, SDM затем вызывает метод [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Метод `IDebugProgramNodeAttach2::OnAttach` возвращается, `S_OK` чтобы указать, что он не прикрепил к программе и что другие попытки могут быть сделаны, чтобы прикрепить к программе.

2. Если SDM может получить интерфейс [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) из прилагаемых программ, SDM вызывает метод [присоединения.](../../extensibility/debugger/reference/idebugprogramex2-attach.md) Такой подход характерен для программ, которые были запущены удаленно поставщиком порта.

3. Если программа не может быть `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` прикреплена с помощью или методов, SDM загружает `CoCreateInstance` отладочный двигатель (если еще не загружен), вызывая функцию, а затем вызывает метод [Присоединения.](../../extensibility/debugger/reference/idebugengine2-attach.md) Такой подход характерен для программ, запущенных на местном уровне поставщиком портов.

    Поставщик портов также может назвать `IDebugEngine2::Attach` этот метод в реализации `IDebugProgramEx2::Attach` метода поставщика пользовательских портов. Обычно в этом случае поставщик порта запускает отладоть двигатель на удаленной машине.

   Прикрепление достигается, когда диспетчер отладки сеанса (SDM) вызывает метод [присоединения.](../../extensibility/debugger/reference/idebugengine2-attach.md)

   Если вы запустите DE в том же процессе, что и приложение для отладки, необходимо реализовать следующие методы [IDebugProgramNode2:](../../extensibility/debugger/reference/idebugprogramnode2.md)

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  После `IDebugEngine2::Attach` вызова метода выполните следующие действия `IDebugEngine2::Attach` в реализации метода:

1. Отправить объект события [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в SDM. Для получения дополнительной информации [см.](../../extensibility/debugger/sending-events.md)

2. Позвоните методу [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) на объекте [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) который был передан методу. `IDebugEngine2::Attach`

     Это возвращает, которое `GUID` используется для идентификации программы. Объект `GUID` должен храниться в объекте, представляющем локальную программу для `IDebugProgram2::GetProgramId` DE, и `IDebugProgram2` он должен быть возвращен при вызове метода на интерфейсе.

    > [!NOTE]
    > При реализации `IDebugProgramNodeAttach2` интерфейса `GUID` программа передается методу. `IDebugProgramNodeAttach2::OnAttach` Это `GUID` используется для `GUID` возврата программы методом. `IDebugProgram2::GetProgramId`

3. Отправить объект события [IDebugProgramCreateEvent2,](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) чтобы уведомить `IDebugProgram2` SDM о том, что локальный объект был создан для представления программы DE. Для получения подробной информации [см.](../../extensibility/debugger/sending-events.md)

    > [!NOTE]
    > Это не тот `IDebugProgram2` объект, который `IDebugEngine2::Attach` был передан в метод. Ранее пройденные `IDebugProgram2` объекты распознаются только портом и является отдельным объектом.

## <a name="see-also"></a>См. также
- [Вложение на основе запуска](../../extensibility/debugger/launch-based-attachment.md)
- [Отправка событий](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
