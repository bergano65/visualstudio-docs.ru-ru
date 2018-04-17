---
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d622397984e6c1b43d1e62852652680b6a6711fb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Считывает указанное число байтов, начиная с указанного относительного виртуального адреса (RVA) из исполняемого файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `relativeVirtualAddress`  
 [in] RVA в исполняемом файле должно начаться чтение.  
  
 `cbData`  
 [in] Число байтов для чтения.  
  
 `pcbData`  
 [out] Возвращает число считанных байтов.  
  
 `data[]`  
 [in, out] Массив, который заполняется байтов, считанных из файла.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается код поддержки доступа к интерфейсу отладки для загрузки данных в байтах из исполняемого файла с помощью относительного виртуального адреса. Этот метод вызывается поддержки [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)