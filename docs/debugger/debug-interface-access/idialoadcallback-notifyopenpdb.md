---
title: IDiaLoadCallback::NotifyOpenPDB | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76a5399a0e473172bb94b22cba813512ccf74014
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920569"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Вызывается, когда кандидат PDB-файл открыт.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdbPath`  
 [in] Полный путь к PDB-файл.  
  
 `resultCode`  
 [in] Код, который указывает на успешное завершение (`S_OK`) или Ошибка загрузки применительно к этому файлу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Код возврата, обычно учитывается.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)