---
title: IDebugProperty3 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ae93a9f88bdee3c4648f803eaf174567fe771c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3"></a>IDebugProperty3
Этот интерфейс обеспечивает поддержку:  
  
-   Получение произвольной длины строки, связанное со свойством.  
  
-   Уникальный идентификатор сопоставление со свойством.  
  
-   Получение списка пользовательских средств просмотра для свойства.  
  
-   Задание значения свойства с возможностью отчетов список ошибок  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс на тот же объект, реализующий [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) для обеспечения поддержки длинных строк, идентификаторы свойств и пользовательских средств просмотра.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProperty2` интерфейс для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от `IDebugProperty2`, `IDebugProperty3` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Возвращает длину строки, связанной со свойством.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Возвращает строку в буфер, предоставленный пользователем.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Создает уникальный идентификатор для этого свойства.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Уничтожает уникальный идентификатор для этого свойства.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Возвращает число пользовательских средств просмотра, можно просматривать это свойство.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Возвращает список пользовательских средств просмотра, можно просматривать это свойство.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Задает значение этого свойства, возвращает сообщение об ошибке, если что-либо пошло не так.|  
  
## <a name="remarks"></a>Примечания  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) является предпочтительным способом для диспетчера сеанса отладки (SDM), чтобы задать значение свойства.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)