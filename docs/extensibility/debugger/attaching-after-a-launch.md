---
title: Присоединение после запуска | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33bc38ca3e0c9b3bde07be48c74c31e4fc5148df
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922220"
---
# <a name="attach-after-a-launch"></a>Присоединение после запуска
После запуска программы сеанса отладки готов для присоединения модуля отладки (DE) для указанной программы.  
  
## <a name="design-decisions"></a>Проектные решения  
 Поскольку взаимодействие происходит проще в общих адресных пространств, необходимо выбрать два подхода к проектированию: установить связь между сеанса отладки и DE. Либо задайте обмен данными между DE и программы. Выберите один из следующих:  
  
-   Если более разумно настройке связи между сеанса отладки и DE, сеанс отладки совместно создает DE и запрашивает DE для присоединения к программе. Такой подход оставляет сеанса отладки и DE вместе в одно адресное пространство и среды выполнения и программы в другой.  
  
-   Если смысл установить связь между DE и программы, среде выполнения совместно создает DE. Такая схема оставляет SDM в одно адресное пространство и DE, среды выполнения и программы в другой. Такой подход является типичным для DE, который реализуется с помощью интерпретатора для запуска сценария языков.  
  
    > [!NOTE]
    >  Как DE присоединяется к программе зависит от реализации. Обмен данными между DE и программы также зависит от реализации.  
  
## <a name="implementation"></a>Реализация  
 Программным образом, когда диспетчер отладки сеансов (SDM) сначала получает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу для запуска, он вызывает [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) метод, передав ему [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) объект, который затем используется для передачи событий отладки SDM. `IDebugProgram2::Attach` Затем вызывает метод [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод. Дополнительные сведения о том, как получает SDM `IDebugProgram2` интерфейсом, см. в разделе [уведомление порта](../../extensibility/debugger/notifying-the-port.md).  
  
 Если ваш DE должна работать в то же адресное пространство, программа отладке: так как DE обычно является частью интерпретатор, на котором выполняется сценарий, `IDebugProgramNodeAttach2::OnAttach` возвращает метод `S_FALSE`. `S_FALSE` Возврата указывает, что он завершен процесс присоединения.  
  
 Если, однако DE выполняется в адресном пространстве SDM: `IDebugProgramNodeAttach2::OnAttach` возвращает `S_OK`, или [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) на вообще не реализовать интерфейс [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с программой отлаживаемым. В этом случае [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) метод в итоге вызывается для завершения операции присоединения.  
  
 В последнем случае необходимо вызвать [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод `IDebugProgram2` объект, который был передан `IDebugEngine2::Attach` метод, магазин `GUID` в локальной программе и не возвращать это `GUID` при `IDebugProgram2::GetProgramId` последующем вызове метода для этого объекта. `GUID` Используется для уникальной идентификации программа различным компонентам отладки.  
  
 В случае использования `IDebugProgramNodeAttach2::OnAttach` метода возвращает `S_FALSE`, `GUID` для программы передается этому методу, и это `IDebugProgramNodeAttach2::OnAttach` метод, который задает `GUID` в объекте локального программы.  
  
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