---
title: IDebugAddress2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 23fb27643a209e870165e521d63079a3b6c650eb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980681"
---
# <a name="idebugaddress2"></a>IDebugAddress2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс обеспечивает доступ к Идентификатору процесса, который является владельцем объекта, адрес которого представлен этим интерфейсом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс. Этот интерфейс обеспечивает доступ к Идентификатору процесса, который является владельцем объекта, который связан с этого адреса.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы vtable  
 Помимо методов, наследуемых от [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс, этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Извлекает идентификатор процесса, которому принадлежит объект, представленный этим интерфейсом.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
