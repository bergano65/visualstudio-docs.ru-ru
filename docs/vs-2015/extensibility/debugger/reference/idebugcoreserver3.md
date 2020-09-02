---
title: IDebugCoreServer3 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1781b133b4c3ee95b4207a0dd237e2dd7298a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685650"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет доступ к сведениям о сервере, в котором выполняется процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из интерфейса [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) . Вызов метода [onserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) может также возвращать этот интерфейс. Этот интерфейс чаще всего используется пользовательским поставщиком портов для запуска программ на сервере (локальном или удаленном).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам в интерфейсе [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[Имя_сервера](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Возвращает имя сервера.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Получает понятную версию имени сервера|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Указывает, что определенные модули отладки автоматически присоединяются к процессам при запуске этих процессов.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Извлекает конкретный код ошибки при сбое автоматического подключения.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Создает экземпляр модуля отладки на сервере.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Получает флаг, указывающий, находится ли сервер на том же компьютере, что и вызывающий объект.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Извлекает значение, указывающее протокол, используемый для связи с сервером.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Отключает все параметры автоматического вложения для всех ядер отладчика, о которых известно этот сервер.|  
  
## <a name="remarks"></a>Remarks  
 Поставщик пользовательского порта получает интерфейс [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) при вызове [события](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3`Интерфейс может быть получен из этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
