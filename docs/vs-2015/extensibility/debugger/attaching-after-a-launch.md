---
title: Подключение после запуска | Документация Майкрософт
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
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843325"
---
# <a name="attaching-after-a-launch"></a>Присоединение после запуска
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

После запуска программы сеанс отладки готов к присоединению модуля отладки (DE) к произнесенной программе.  
  
## <a name="design-decisions"></a>Проектные решения  
 Так как обмен данными в рамках общего адресного пространства упрощается, необходимо решить, имеет ли он более разумный способ упрощения обмена данными между сеансом отладки и DE, а также между DE и программой. Выберите один из следующих:  
  
- Если есть смысл упростить обмен данными между сеансом отладки и DE, то сеанс отладки совместно создает сообщение DE и запрашивает отключение к программе. Это оставляет сеанс отладки и разключается в одном адресном пространстве, а среда выполнения и программа — вместе друг с другом.  
  
- Если есть смысл упростить обмен данными между DE и программой, среда выполнения совместно создает значение DE. Это оставляет SDM в одном адресном пространстве, а также в среде выполнения, а затем вместе с другими программами. Это типичная часть DE, реализованная с интерпретатором для выполнения сценариев языков.  
  
    > [!NOTE]
    > То, как DE присоединяется к программе, зависит от реализации. Связь между DE и программой также зависит от реализации.  
  
## <a name="implementation"></a>Реализация  
 Программным способом, когда диспетчер отладки сеансов (SDM) сначала получает объект [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , представляющий запускаемую программу, он вызывает метод [attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , передавая ему объект [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , который позже используется для передачи событий отладки в SDM. `IDebugProgram2::Attach`Затем метод вызывает метод [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Дополнительные сведения о том, как SDM получает `IDebugProgram2` интерфейс, см. [в разделе уведомление порта](../../extensibility/debugger/notifying-the-port.md).  
  
 Если ваш DE должен выполняться в том же адресном пространстве, что и отлаживаемая программа, как правило, поскольку DE является частью интерпретатора, выполняющего сценарий, `IDebugProgramNodeAttach2::OnAttach` метод возвращает значение `S_FALSE` , указывающее, что он завершил процесс присоединения.  
  
 Если, с другой стороны, выполняет DE в адресном пространстве SDM, `IDebugProgramNodeAttach2::OnAttach` метод возвращает `S_OK` или интерфейс [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) не реализуется вообще для объекта [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , связанного с отлаживаемой программой. В этом случае метод [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается в конечном итоге для завершения операции присоединения.  
  
 В последнем случае необходимо вызвать метод [жетпрограмид](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) для `IDebugProgram2` объекта, переданного в `IDebugEngine2::Attach` метод, сохранить `GUID` в локальном объекте Program и вернуть его `GUID` при `IDebugProgram2::GetProgramId` последующем вызове метода для этого объекта. `GUID`Используется для однозначной идентификации программы в различных компонентах отладки.  
  
 Обратите внимание, что в случае `IDebugProgramNodeAttach2::OnAttach` возврата метода, который будет `S_FALSE` `GUID` использоваться для программы, передается в этот метод и является `IDebugProgramNodeAttach2::OnAttach` методом, устанавливающим `GUID` объект для локального объекта Program.  
  
 Теперь программа DE подключена к программе и готова к отправке любых событий запуска.  
  
## <a name="see-also"></a>См. также:  
 [Прямое подключение к программе](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Уведомление порта](../../extensibility/debugger/notifying-the-port.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Вновь](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [жетпрограмид](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Присоединение](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
