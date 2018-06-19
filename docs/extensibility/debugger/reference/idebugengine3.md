---
title: IDebugEngine3 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 291f5ca6f945abe9e0322839eb80c38b60674ce4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114421"
---
# <a name="idebugengine3"></a>IDebugEngine3
Представляет обработчик одной отладки (DE), который управляет отладки один или несколько модулей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется пользовательский DE (если он поддерживает символы) чтобы включить состояние JustMyCode. Этот интерфейс должен быть реализован, DE, если он поддерживает символы и JustMyCode.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс называется диспетчером сеанса отладки (SDM) для передачи параметров с пользователем для расположения, из которого требуется загрузить символы. Он также называется задаваемое GUID модуля при его создании экземпляра (идентификатор GUID формируется на основе из ядра регистрации). SDM также вызывает этот интерфейс для задания состояния JustMyCode и задать все исключения, известные отладчиком в определенное состояние.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Задает путь или пути, DE будет использовать для поиска символов отладки.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Загрузка символов для всех модулей, которые еще не было их загруженные символы.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|DE сообщает о JustMyCode сведения.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Задает идентификатор GUID DE из метрики.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Задайте указанное состояние необработанный все исключения.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)