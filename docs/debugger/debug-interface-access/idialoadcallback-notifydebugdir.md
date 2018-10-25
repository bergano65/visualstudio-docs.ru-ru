---
title: IDiaLoadCallback::NotifyDebugDir | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdceb0f1f07a3ef9d22dbd30a02b2558c4d81603
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950879"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Вызывается, когда был найден каталог отладки в файл .exe.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
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