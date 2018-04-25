---
title: IDiaStackWalkHelper::get_registerValue | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ccc491ec9e966b8d893b6d669aafc64ebc5c8cf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
Извлекает значение регистра.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Значение из [перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) указание которой зарегистрироваться и получить значение из перечисления.  
  
 `pRetVal`  
 [out] Возвращает текущее значение регистра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Несмотря на размер `pRetVal` параметра реализацию следует хранить только регистр обычно содержат. Например 8-битный регистр содержит только младшие 8-битов заданного значения. Это значение 8-разрядного расширяется до 64 бит при возврате из этого метода.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)