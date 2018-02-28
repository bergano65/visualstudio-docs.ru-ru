---
title: "IDiaLoadCallback | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5cc40b8041ea5427d223a70c7d3d9347c48be286
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Получает обратные вызовы от символа DIA поиск процедур, что позволяет пользовательский интерфейс для отчетов о ходе попытки расположение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Следующие методы предоставляемые этим интерфейсом:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Вызывается, когда каталог отладки был найден в файле .exe.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Вызывается, когда файл .dbg кандидат был открыт.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Вызывается, когда кандидат PDB-файл был открыт.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Определяет, если реестра запросы могут быть использованы для поиска пути поиска символов.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Определяет, если доступ будет разрешен на сервере символов для разрешения символов.|  
  
## <a name="remarks"></a>Примечания  
 Клиентское приложение реализует этот интерфейс и предоставляет ссылку на него в вызове [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
 Дополнительные ограничения, которые могут быть наложены на процесса загрузки см. в разделе [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)