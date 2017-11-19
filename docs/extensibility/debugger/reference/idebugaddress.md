---
title: "IDebugAddress | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress
helpviewer_keywords: IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f009002e9c454b1e10cac13c297e067da9c44ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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