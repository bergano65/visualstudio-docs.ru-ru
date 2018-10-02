---
title: IDiaLoadCallback::NotifyDebugDir | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4496a7941de29f4ef500a135559dcd746036f6d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572651"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaLoadCallback::NotifyDebugDir](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-notifydebugdir).  
  
Вызывается, когда был найден каталог отладки в файл .exe.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fExecutable`  
 [in] `TRUE` Если каталога отладки считывается из исполняемого файла (а не файл .dbg).  
  
 `cbData`  
 [in] Число байтов данных в каталоге отладки.  
  
 `data[]`  
 [in] Массив, который заполняется каталога отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Код возврата, обычно учитывается.  
  
## <a name="remarks"></a>Примечания  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод вызывает этот обратный вызов при обнаружении каталога отладки при обработке исполняемый файл.  
  
 Этот метод избавляет от необходимости для поддержки отладки не найден в PDB-файл для клиента, чтобы реконструировать файле исполняемый файл и/или отладки. С этими данными клиент может распознать тип отладочных данных, доступных и он находится в исполняемый файл или файл .dbg.  
  
 Большинство клиентов не потребуется этот обратный вызов, так как `IDiaDataSource::loadDataForExe` метод прозрачно открывает файлы PDB-файл и .dbg, при необходимости обрабатывать символы.  
  
## <a name="see-also"></a>См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



