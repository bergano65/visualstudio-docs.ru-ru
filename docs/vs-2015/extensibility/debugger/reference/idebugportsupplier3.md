---
title: IDebugPortSupplier3 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ece720cf6880bba528dee99cdbdeb25c10087a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674133"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс позволяет вызывающему объекту определить, может ли поставщик порта сохранять порты (путем записи их на диск) между вызовами отладчика, а затем получать список сохраненных портов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Пользовательский поставщик портов реализует этот интерфейс для поддержки сохранения или сохранения сведений о портах на диск. Этот интерфейс должен быть реализован на том же объекте, что и интерфейс [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) в `IDebugPortSupplier2` интерфейсе, чтобы получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 В дополнение к методам, унаследованным от интерфейса [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , этот интерфейс поддерживает следующие действия:  
  
|Метод|Описание|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Возвращает значение, указывающее, может ли поставщик порта сохранять порты (путем записи на диск) между вызовами отладчика.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Возвращает объект, который можно использовать для перечисления всех портов, записанных на диск этим поставщиком портов.|  
  
## <a name="remarks"></a>Remarks  
 Если поставщик порта может сохранять порты между вызовами, он должен реализовать этот интерфейс. Порты должны быть загружены при создании экземпляра поставщика порта и записаны на диск при уничтожении поставщика порта.  
  
 Модуль отладки обычно не взаимодействует с поставщиком порта и не будет использовать его для этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
