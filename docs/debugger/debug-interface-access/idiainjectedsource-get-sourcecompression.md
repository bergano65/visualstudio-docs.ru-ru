---
title: IDiaInjectedSource::get_sourceCompression | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e3a769dd41d9787a278c7a3f72c31efcbd8a445
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Возвращает признак источник сжатия, используемый.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает индикатор источник сжатия. Нулевое значение указывает, использование сжатия не источника.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает значение для компилятора. Например компилятор может использовать сжатие длин кодирования или Хаффмана стиль.  
  
## <a name="see-also"></a>См. также  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)