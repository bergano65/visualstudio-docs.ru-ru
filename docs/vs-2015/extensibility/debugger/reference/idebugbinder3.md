---
title: IDebugBinder3 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 406207d070d64bcd5e26670930d94a72cf3f8595
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200373"
---
# <a name="idebugbinder3"></a>IDebugBinder3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс обеспечивает доступ к типам, псевдонимы и пользовательский визуализатор служб.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для поддержки псевдонимы пользовательский визуализатор и службы доступа к информации типа объекта.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс получает этот интерфейс с помощью [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, предоставляемых [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс, этот интерфейс реализует следующее:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Извлекает объект памяти, представляющий памяти, с которым связан этот объект.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Получает исключение, связанное с объектом (если таковые имеются),|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Получает псевдонимы по имени|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Извлекает массив все псевдонимы для этого объекта|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Возвращает количество типов аргументов, связанный с данным объектом|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Извлекает список типов аргументов, связанный с данным объектом|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Возвращает интерфейс к службе визуализатора|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Преобразует адрес объекта или адрес памяти 64-разрядной памяти контекста.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)

