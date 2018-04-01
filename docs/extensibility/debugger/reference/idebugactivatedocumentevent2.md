---
title: IDebugActivateDocumentEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c6ace15a6e2a88aa214261d3d8ec137ebb6d7ebe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Модуль отладки (DE) использует этот интерфейс для запроса загрузить документ.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс, когда он должен исходный файл, чтобы открыть. Этот интерфейс реализуется только отладчики, которые работы, или являются частью интерпретаторов скрипта. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события, когда он должен иметь исходный файл открыт. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugActivateDocumentEvent2`.  
  
|Методы|Описание:|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Получает документ для активации.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Возвращает контекст документ, описывающий позицию в документе.|  
  
## <a name="remarks"></a>Примечания  
 Типичный сценарий, в котором используется этот интерфейс является при возникновении ошибки синтаксического анализа в коде скрипта на HTML-страницы, скрипт DE отправляет этот интерфейс SDM для отображения документа с Ошибка синтаксического анализа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)