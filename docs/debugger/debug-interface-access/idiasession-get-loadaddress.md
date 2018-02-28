---
title: "IDiaSession::get_loadAddress | Документы Microsoft"
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
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ff72da3cd9c39dd12e2fc07d6851a4bee98fd48c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
Извлекает адрес загрузки для исполняемого файла, соответствующее символов в данном хранилище символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает виртуальный адрес (VA), в которой загружается файл .exe или DLL-файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Адрес возвращаемый нагрузки всегда будет равно нулю, если только специально настроены с помощью [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)