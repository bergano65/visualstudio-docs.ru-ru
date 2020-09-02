---
title: 'Идиалоадкаллбакк:: Нотифидебугдир | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151998"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вызывается при обнаружении каталога отладки в exe-файле.  
  
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
 [входные] `TRUE` значение, если каталог отладки считывается из исполняемого файла (а не DBG-файлов).  
  
 `cbData`  
 окне Число байтов данных в каталоге отладки.  
  
 `data[]`  
 окне Массив, который заполняется каталогом отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Код возврата обычно игнорируется.  
  
## <a name="remarks"></a>Remarks  
 Метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) вызывает этот обратный вызов при обнаружении каталога отладки во время обработки исполняемого файла.  
  
 Этот метод устраняет потребность клиента в реконструировании исполняемого файла и/или файл отладки для поддержки отладочной информации, отличной от найденной в PDB-файле. С этими данными клиент может распознать тип доступных отладочных сведений и определить, находится ли он в исполняемом или DBG файле.  
  
 Большинству клиентов этот обратный вызов не нужен, поскольку `IDiaDataSource::loadDataForExe` метод прозрачно открывает файлы PDB и dbg при необходимости для обслуживания символов.  
  
## <a name="see-also"></a>См. также:  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
