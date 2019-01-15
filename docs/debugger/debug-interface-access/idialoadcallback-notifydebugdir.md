---
title: IDiaLoadCallback::NotifyDebugDir | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 7fe328d9f77871692f04d13fba533517c3cc12f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958921"
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
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)