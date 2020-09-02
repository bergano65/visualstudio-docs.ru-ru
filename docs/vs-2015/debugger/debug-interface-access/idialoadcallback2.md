---
title: IDiaLoadCallback2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5c1225d75ea857fe34906daeb4792524fde4bc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538815"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает обратные вызовы из процедуры поиска символов DIA, позволяя налагать ограничения на процесс обнаружения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам в интерфейсе [идиалоадкаллбакк](../../debugger/debug-interface-access/idialoadcallback.md) этот интерфейс предоставляет следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Определяет, искать ли PDB-файл в исходном каталоге отладки.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Определяет, разрешен ли PDB-файл в пути, где находится EXE-файл.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Определяет, разрешена ли информация об отладке из DBG-файлов.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Определяет, разрешен ли поиск PDB-файлов в корневом каталоге системы.|  
  
## <a name="remarks"></a>Remarks  
 Клиентское приложение реализует этот интерфейс и предоставляет ссылку на него в вызове метода [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) . Не забывайте также реализовать все методы в интерфейсе [идиалоадкаллбакк](../../debugger/debug-interface-access/idialoadcallback.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Идиадатасаурце:: Лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
