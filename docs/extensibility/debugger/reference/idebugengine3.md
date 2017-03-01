---
title: "IDebugEngine3 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 293517b87b57e905e5807fa9e3f07a47d4cead4c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3"></a>IDebugEngine3
Представляет механизм единого отладки (DE), который управляет отладки один или несколько модулей.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется пользовательский DE (если он поддерживает символы) для включения JustMyCode состояния. Этот интерфейс должен быть реализован DE, если он поддерживает символы и JustMyCode.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс называется диспетчером сеанса отладки (SDM) для передачи пользовательских параметров для местоположения, откуда загружать символы. Он также вызывается для задания GUID модуля при создании экземпляра (этот идентификатор GUID формируется на основе времени регистрации обработчика). SDM также вызывает этот интерфейс для установки состояния JustMyCode и установить все исключения, известные отладчиком для указанного состояния.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), `IDebugEngine3` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Задает путь или пути, DE будет использовать для поиска символов отладки.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Загрузка символов для всех модулей, которые еще не были загружены символы, их.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|DE сообщает о JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Задает идентификатор GUID DE на основе метрик.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Задайте указанное состояние ожидающих все исключения.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
