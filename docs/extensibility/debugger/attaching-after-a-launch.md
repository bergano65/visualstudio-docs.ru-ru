---
title: "Присоединение после запуска | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a06a9b4be6cb20339c8c89f8594f290c1f6a46a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="attaching-after-a-launch"></a>Присоединение после запуска
После запуска программы сеанса отладки готов для присоединения модуля отладки (DE) для данной программы.  
  
## <a name="design-decisions"></a>Проектные решения  
 Поскольку коммуникация становится проще в общее адресное пространство, необходимо решить, ли смысл для взаимодействия между сеанса отладки "и" DE "или между DE и программой. Выберите один из следующих:  
  
-   Если смысл для упрощения взаимодействия между сеанса отладки "и" DE ", сеанс отладки совместно создает DE и запрашивает DE для присоединения к программе. Это оставляет сеанс отладки и DE вместе в одно адресное пространство и среды выполнения и программы в другой.  
  
-   Если смысл для упрощения взаимодействия между DE и программы, среда выполнения совместно создает DE. Это оставляет SDM в одно адресное пространство и DE, среды выполнения и программы в другой. Это характерно для DE, реализованный интерпретатор для запуска сценария языков.  
  
    > [!NOTE]
    >  Как DE присоединяет к программе зависит от реализации. Обмен данными между DE и программы также зависят от реализации.  
  
## <a name="implementation"></a>Реализация  
 Программно, когда диспетчер сеанса отладки (SDM) сначала получает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу для запуска, он вызывает [присоединение](../../extensibility/debugger/reference/idebugprogram2-attach.md) метод, передав ему [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) объекта, который затем используется для передачи событий отладки SDM. `IDebugProgram2::Attach` Затем вызывает метод [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод. Дополнительные сведения о том, как получает SDM `IDebugProgram2` интерфейса см. в разделе [уведомление порт](../../extensibility/debugger/notifying-the-port.md).  
  
 Если ваш DE должна работать в том же адресном пространстве как отлаживаемой программы, обычно из-за DE является частью интерпретатор выполнения сценария, `IDebugProgramNodeAttach2::OnAttach` возвращает `S_FALSE`, указывающее на завершение процесса подключения.  
  
 Если, с другой стороны, DE выполняется в адресном пространстве SDM `IDebugProgramNodeAttach2::OnAttach` возвращает `S_OK` или [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) интерфейса не реализован вообще на [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) объект, связанный с отлаживаемой программы. В этом случае [присоединение](../../extensibility/debugger/reference/idebugengine2-attach.md) метод в конечном счете вызывается для завершения операции присоединения.  
  
 В последнем случае необходимо вызвать [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) метод `IDebugProgram2` объект, который был передан в `IDebugEngine2::Attach` метод, хранилища `GUID` в локальной программе и возвращать это `GUID` при `IDebugProgram2::GetProgramId` будет впоследствии вызван для этого объекта. `GUID` Используется для уникальной идентификации различным компонентам отладки программы.  
  
 Обратите внимание, что в случае использования `IDebugProgramNodeAttach2::OnAttach` метод, возвращающий `S_FALSE`, `GUID` для программы передается этому методу, а это `IDebugProgramNodeAttach2::OnAttach` метод, который задает `GUID` в объекте программ.  
  
 DE теперь подключен к программе и готовы к отправке все события запуска.  
  
## <a name="see-also"></a>См. также  
 [Подключение к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Уведомление порт](../../extensibility/debugger/notifying-the-port.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Присоединение](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)