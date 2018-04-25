---
title: IDiaLoadCallback::NotifyDebugDir | Документы Microsoft
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
ms.openlocfilehash: 46621c667967f0b87d197839012e830207cc306a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Вызывается, когда каталог отладки был найден в файле .exe.  
  
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
 [in] `TRUE` Если каталог отладки считывается из исполняемого файла (а не файл .dbg).  
  
 `cbData`  
 [in] Число байт данных в каталоге отладки.  
  
 `data[]`  
 [in] Массив, который содержит каталог отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Код возврата, обычно учитывается.  
  
## <a name="remarks"></a>Примечания  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод вызывает этот обратный вызов, когда находит каталог отладки при обработке исполняемого файла.  
  
 Этот метод удаляет необходимость для клиента реконструировать исполняемый файл и (или) отладки файл отладочной информации, отличный от того, в PDB-файл. На основе этих данных клиент может распознать тип отладочной информации, и он находится в исполняемый файл или файл .dbg.  
  
 Большинство клиентов не требуется этот обратный вызов, так как `IDiaDataSource::loadDataForExe` метод прозрачно открывает PDB-файл и .dbg файлы при необходимости обрабатывать символы.  
  
## <a name="see-also"></a>См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)