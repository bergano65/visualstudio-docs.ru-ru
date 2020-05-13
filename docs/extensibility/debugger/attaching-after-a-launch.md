---
title: Прикрепление после запуска (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739287"
---
# <a name="attach-after-a-launch"></a>Прикрепить после запуска
После запуска программы сеанс отладки готов прикрепить движок отладки (DE) к указанной программе.

## <a name="design-decisions"></a>Проектные решения
 Поскольку общение проще в общем пространстве адреса, необходимо выбрать между двумя подходами к проектированию: набор связи между сеансом отладки и DE. Или установите связь между DE и программой. Выберите между следующими:

- Если имеет смысл настроить связь между сеансом отладки и DE, сеанс отладки является со-создаем DE и просит DE прикрепить ее к программе. Эта конструкция оставляет сеанс отладки и DE вместе в одном адресном пространстве, а среда и программа выполнения — вместе в другом.

- Если имеет смысл настроить связь между DE и программой, среда времени выполнения совместно создает DE. Эта конструкция оставляет SDM в одном адресном пространстве и DE, среду времени выполнения и программировать вместе в другом. Эта конструкция типична для DE, который реализуется с помощью переводчика для запуска языков со сценарием.

    > [!NOTE]
    > То, как DE прикрепляется к программе, зависит от реализации. Связь между DE и программой также зависит от реализации.

## <a name="implementation"></a>Реализация
 Программно, когда менеджер отладки сеанса (SDM) сначала получает объект [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) представляющий запущенную программу, он вызывает метод [присоединения,](../../extensibility/debugger/reference/idebugprogram2-attach.md) передав его [объектi IDebugEventCallback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) который позже используется для передачи событий отладки обратно в SDM. Затем `IDebugProgram2::Attach` метод вызывает метод [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Для получения дополнительной информации о `IDebugProgram2` том, как SDM получает интерфейс, см. [Notifying the port](../../extensibility/debugger/notifying-the-port.md)

 Если DE необходимо работать в том же адресном пространстве, что и программа, которую вы отлажаете: `IDebugProgramNodeAttach2::OnAttach` поскольку DE обычно является частью устного переводчика, работающего с скриптом, метод возвращается. `S_FALSE` Возврат `S_FALSE` указывает на то, что он завершил процесс присоединения.

 Однако, если DE работает в адресном пространстве `IDebugProgramNodeAttach2::OnAttach` SDM: метод возвращается `S_OK`или интерфейс [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) вообще не реализован на объекте [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) связанном с отладкой программы. В этом случае метод [присоединения](../../extensibility/debugger/reference/idebugengine2-attach.md) в конечном итоге вызывается для завершения операции присоединения.

 В последнем случае необходимо вызвать метод [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) на `IDebugProgram2` объекте, который был передан `IDebugEngine2::Attach` методу, хранить `GUID` объект локальной программы и вернуть его, `GUID` когда `IDebugProgram2::GetProgramId` метод впоследствии вызывается на этот объект. Используется `GUID` для идентификации программы однозначно через различные компоненты отладки.

 В случае возврата `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` `GUID` метода, использование программы передается этому методу, и `IDebugProgramNodeAttach2::OnAttach` это метод, который устанавливает `GUID` на локальном объекте программы.

 DE теперь прилагается к программе и готов отправить любые события запуска.

## <a name="see-also"></a>См. также
- [Присоединение непосредственно к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Уведомление порта](../../extensibility/debugger/notifying-the-port.md)
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
