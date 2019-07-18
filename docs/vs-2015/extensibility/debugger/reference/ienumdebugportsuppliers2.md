---
title: IEnumDebugPortSuppliers2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f8ed12c0ba9c6263968c51a7e8cfcdfe2fe47011
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179155"
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс перечисляет поставщики портов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для представления списка поставщиков порт.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) для получения списка поставщиков порт.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugPortSuppliers2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Извлекает указанное число поставщикам портов в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Пропускает заданное число поставщиков портов в последовательности перечисления.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Получает номер порта поставщиков в перечислителе.|  
  
## <a name="remarks"></a>Примечания  
 Модуль отладки, как правило, необязательно для получения этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)
