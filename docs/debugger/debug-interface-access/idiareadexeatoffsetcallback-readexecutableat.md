---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Документы Microsoft"
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
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1250bef977c887be9d4d98fb4372a597c4e22072
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Считывает указанное число байтов, начиная с заданного смещения из исполняемого файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 fileOffset  
 [in] Смещение в исполняемом файле, должно начаться чтение.  
  
 cbData  
 [in] Число байтов для чтения.  
  
 pcbData  
 [out] Возвращает число считанных байтов.  
  
 данные]  
 [in, out] Массив, который заполняется байтов, считанных из файла.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается код поддержки доступа к интерфейсу отладки для загрузки данных в байтах из исполняемого файла с помощью абсолютный смещение. Этот метод вызывается поддержки [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)