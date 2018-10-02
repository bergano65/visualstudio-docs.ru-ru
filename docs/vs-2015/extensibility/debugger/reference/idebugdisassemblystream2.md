---
title: IDebugDisassemblyStream2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f72cea28e47bdd14681c1f843a2620a43162885
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571547"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugDisassemblyStream2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2).  
  
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

