---
title: IDebugProperty3 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 479827cc83486d6bb9c68d0749b8870cd6c41861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694763"
---
# <a name="idebugproperty3"></a>IDebugProperty3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс обеспечивает поддержку:  
  
- Извлечение произвольно длинной строки, связанной со свойством.  
  
- Связывание уникального идентификатора со свойством.  
  
- Получение списка пользовательских средств просмотра для свойства.  
  
- Установка значения свойства с возможностью сообщать о любых возникших ошибках  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для того же объекта, который реализует [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , чтобы обеспечить поддержку длинных строк, идентификаторов свойств и пользовательских средств просмотра.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для `IDebugProperty2` интерфейса, чтобы получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам, унаследованным от `IDebugProperty2` , `IDebugProperty3` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Возвращает длину строки, связанной со свойством.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Возвращает строку в предоставляемом пользователем буфере.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Создает уникальный идентификатор для этого свойства.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Уничтожает уникальный идентификатор для этого свойства.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Возвращает число пользовательских средств просмотра, с которыми можно просмотреть это свойство.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Возвращает список пользовательских средств просмотра, с которыми можно просмотреть это свойство.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Задает значение этого свойства, возвращая сообщение об ошибке, если что-то пошло не так.|  
  
## <a name="remarks"></a>Remarks  
 [Сетвалуеасстрингвисеррор](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) является предпочтительным способом, который диспетчер отладки сеанса (SDM) задает значение свойства.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
