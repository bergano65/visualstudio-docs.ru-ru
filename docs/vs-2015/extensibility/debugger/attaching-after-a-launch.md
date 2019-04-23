---
title: Присоединение после запуска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 71b26fc2d26e180af25919dde5d3c4ee1bc1f891
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113122"
---
# <a name="attaching-after-a-launch"></a>Присоединение после запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После запуска программы, сеанс отладки готов для присоединения модуля отладки (DE) для указанной программы.  
  
## <a name="design-decisions"></a>Проектные решения  
 Поскольку взаимодействие происходит проще в общих адресных пространств, необходимо решить, ли смысл для упрощения взаимодействия между сеанса отладки и DE или между DE и программой. Выберите один из следующих:  
  
- Если более разумно для упрощения взаимодействия между сеанса отладки и DE, сеанс отладки совместно создает DE и запрашивает DE для присоединения к программе. При этом сеанс отладки и DE вместе в одно адресное пространство и среды выполнения и программы в другой.  
  
- Если смысл для упрощения взаимодействия между DE и программой, среда выполнения совместно создает DE. Это оставляет SDM в одно адресное пространство и DE, среды выполнения и программы в другой. Это характерно для DE, который реализуется с помощью интерпретатора для запуска сценария языков.  
  
    > [!NOTE]
    >  Как DE присоединяется к программе зависит от реализации. Обмен данными между DE и программы также зависит от реализации.  
  
## <a name="implementation"></a>Реализация  
 Программным образом, когда диспетчер отладки сеансов (SDM) сначала получает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу для запуска, он вызывает [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) метод, передав ему [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) объект, который затем используется для передачи событий отладки SDM. `IDebugProgram2::Attach` Затем вызывает метод [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод. Дополнительные сведения о том, как получает SDM `IDebugProgram2` интерфейсом, см. в разделе [уведомление порта](../../extensibility/debugger/notifying-the-port.md).  
  
 Если ваш DE должна работать в то же адресное пространство как отлаживаемой программы, обычно потому, что DE является частью выполнения сценария, интерпретатор `IDebugProgramNodeAttach2::OnAttach` возвращает метод `S_FALSE`, указывающее на то, что оно выполнено процесс присоединения.  
  
 Если, с другой стороны, DE выполняется в адресном пространстве SDM, `IDebugProgramNodeAttach2::OnAttach` возвращает `S_OK` или [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейса не реализован вообще на [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с отлаживаемой программы. В этом случае [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод в итоге вызывается для завершения операции присоединения.  
  
 В последнем случае необходимо вызвать [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод `IDebugProgram2` объект, который был передан `IDebugEngine2::Attach` метод, магазин `GUID` в локальной программе и не возвращать это `GUID` при `IDebugProgram2::GetProgramId` последующем вызове метода для этого объекта. `GUID` Используется для уникальной идентификации программа различным компонентам отладки.  
  
 Обратите внимание, что в случае использования `IDebugProgramNodeAttach2::OnAttach` метода возвращает `S_FALSE`, `GUID` для программы передается этому методу, и это `IDebugProgramNodeAttach2::OnAttach` метод, который задает `GUID` в объекте локального программы.  
  
 DE теперь подключен к программе и готов отправить все события запуска.  
  
## <a name="see-also"></a>См. также  
 [Подключение к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Уведомление порта](../../extensibility/debugger/notifying-the-port.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Присоединение](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
