---
title: "IDiaReadExeAtOffsetCallback | Документы Microsoft"
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
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abb829d12f05a9c220bc22647659c438180d237e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Позволяет клиентскому приложению для предоставления байт исполняемого файла в соответствии с позиции в файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDiaReadExeAtOffsetCallback`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Считывает указанное число байтов, начиная с заданного смещения из исполняемого файла.|  
  
## <a name="remarks"></a>Примечания  
 Клиентское приложение реализует этот интерфейс, чтобы обеспечить байты исполняемого файла с помощью абсолютный смещение в исполняемый файл. Чтобы использовать относительный виртуальный адрес, реализовать [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот метод реализуется клиентским приложением и переданный [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод как альтернативный метод для чтения этого файла.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia80.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)