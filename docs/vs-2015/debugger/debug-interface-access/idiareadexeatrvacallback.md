---
title: Идиареадексеатрвакаллбакк | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8275756a4b89ab56148a9f7b560eda5d671fc6a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150580"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Позволяет клиентскому приложению предоставлять байты исполняемого файла, как указано в относительном виртуальном адресе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaReadExeAtRVACallback` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Считывает указанное число байтов, начиная с указанного относительного виртуального адреса (RVA) из исполняемого файла.|  
  
## <a name="remarks"></a>Remarks  
 Клиентское приложение реализует этот интерфейс, чтобы предоставить байты исполняемого файла по относительному виртуальному адресу в исполняемый файл. Чтобы использовать абсолютное смещение файла, реализуйте интерфейс [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот метод реализуется клиентским приложением и передается методу [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) в качестве альтернативного метода чтения файла.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Идиадатасаурце:: Лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
