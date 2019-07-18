---
title: IDebugModule3 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 326efe27ae35de1550ebc8230ab3c94229589640
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690956"
---
# <a name="idebugmodule3"></a>IDebugModule3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет модуль, который поддерживает альтернативные расположения символов и JustMyCode состояний.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для поддержки альтернативные расположения символов и для работы с состояниями JustMyCode (см. в разделе [глоссарий отладчика Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) определение «JustMyCode»).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) возвращает этот интерфейс. Отправляет DE [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) интерфейс для сеанса отладки manager (SDM) с помощью [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод. Кроме того, вызов [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) интерфейс возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Возвращает список путей поиска символов и результаты поиска каждого пути.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Загружает и инициализирует символов для текущего модуля.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Возвращает флаг, указывающий, представляет ли модуль пользовательским кодом.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Указывает, следует ли учитывать модуль пользовательским кодом или нет.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio является типичного потребителя этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
