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
ms.openlocfilehash: c127bdb807b397060342bf7051c3c0de1251627f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978735"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет доступ к информации о сервере, в которой выполняется процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Используйте [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс. Вызов [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) также может возвращать этот интерфейс. Этот интерфейс используется чаще всего поставщика пользовательского порта для запуска программ на сервере (локальных или удаленных).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Извлекает имя сервера.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Извлекает понятная версия имени сервера|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Сообщает о конкретных отладчиков, чтобы автоматически подключиться к процессам, при запуске этих процессов.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Возвращает конкретный код ошибки, если автоматическое присоединение завершается с ошибкой.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Создает экземпляр модуля отладки на сервере.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Получает флаг, указывающий, является ли сервер на том же компьютере, что и вызывающий объект.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Получает значение, указывающее протокол, используемый для связи с сервером.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Отключает все автоприсоединение параметры для всех обработчиков отладки, этот сервер знает.|  
  
## <a name="remarks"></a>Примечания  
 Получает поставщика пользовательского порта [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейса во время вызова [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3` Интерфейса можно получить из этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
