---
title: "IDiaLoadCallback::NotifyOpenPDB | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0767be9a51c0d5c3395df9586c5c646a41b78e7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Вызывается при открытии кандидата PDB-файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdbPath`  
 [in] Полный путь к PDB-файлу.  
  
 `resultCode`  
 [in] Код, который указывает на успешное завершение (`S_OK`) или сбоя загрузки применительно к этому файлу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Код возврата, обычно учитывается.  
  
## <a name="see-also"></a>См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)