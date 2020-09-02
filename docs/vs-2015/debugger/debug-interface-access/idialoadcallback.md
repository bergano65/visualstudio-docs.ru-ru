---
title: Идиалоадкаллбакк | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b26a638c1ac8bd808bae6fa78aaa3cc24dedede5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151968"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает обратные вызовы из процедуры поиска символов DIA, тем самым позволяя пользовательскому интерфейсу сообщать о ходе попытки расположения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Этот интерфейс представляет следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Вызывается при обнаружении каталога отладки в exe-файле.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Вызывается при открытии файла Candidate. dbg.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Вызывается при открытии файла Candidate. pdb.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Определяет, могут ли запросы к реестру использоваться для определения путей поиска символов.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Определяет, разрешен ли доступ к серверу символов для разрешения символов.|  
  
## <a name="remarks"></a>Remarks  
 Клиентское приложение реализует этот интерфейс и предоставляет ссылку на него в вызове метода [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Дополнительные ограничения, которые могут быть наложены на процесс загрузки, см. в разделе интерфейс [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Идиадатасаурце:: Лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
