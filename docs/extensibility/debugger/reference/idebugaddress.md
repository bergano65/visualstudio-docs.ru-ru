---
title: IDebugAddress | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ace2892d4518de8c5a4abaa2c113df914f9fa6b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaddress"></a>IDebugAddress
Этот интерфейс представляет собой адрес элемента. Он возвращается в виде обработчика символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс для представления адрес объекта.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Множество методов для многих интерфейсов возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Извлекает [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура, описывающая объект и его расположение.|  
  
## <a name="remarks"></a>Примечания  
 Символ поставщик возвращает этот интерфейс для представления объекта и его расположение в определенной области (например, функции, метода или класса). Этот интерфейс возвращается из и различные методы поставщика символов и выражения, передаваемый оценки. Как правило поставщик символ является единственной сущностью, который должен интерпретировать содержимое этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)