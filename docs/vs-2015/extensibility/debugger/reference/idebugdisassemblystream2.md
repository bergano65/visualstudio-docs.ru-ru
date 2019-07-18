---
title: IDebugDisassemblyStream2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5126758c60262564390f84b6278300a41660f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187172"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет поток инструкций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для поддержки Дизассемблированный код программного кода.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) метод возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDisassemblyStream2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Считывает инструкциям, начиная с текущей позиции в потоке Дизассемблированный код.|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Перемещает указатель чтения в потоке дизассемблированного кода заданного числа инструкции относительно указанной позиции.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Возвращает идентификатор расположения кода для контекста кода.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Возвращает объект контекста кода, соответствующий идентификатору расположение указанного кода.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Возвращает идентификатор расположения кода, который представляет текущее расположение кода.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Возвращает исходный документ, связанный с этого потока Дизассемблированный код.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Получает область этого потока Дизассемблированный код.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Получает размер этого потока Дизассемблированный код.|  
  
## <a name="remarks"></a>Примечания  
 Можно создать поток Дизассемблированный код для представления во всем адресном пространстве или просто функции или модуля в пространстве. Каждая инструкция, представленного [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) структуры, возвращенный вызовом к [чтения](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
