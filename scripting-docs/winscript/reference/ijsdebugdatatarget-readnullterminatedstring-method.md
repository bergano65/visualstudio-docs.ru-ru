---
title: "Метод IJsDebugDataTarget::ReadNullTerminatedString | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94cb90b8b44aa5dab13a2e916dec22ae950e77ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Метод IJsDebugDataTarget::ReadNullTerminatedString
Считывает указанное количество символов из целевого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 [in] Адрес, из которого выполняется чтение.  
  
 `characterSize`  
 [in] размер каждого символа в строке  
  
 `maxCharacters`  
 [in] Максимальное число считываемых символов. maxCharacters должен быть разумным. Любой запрос для более чем 128 МБ памяти завершится ошибкой.  Если строки больше, чем maxCharacters, после maxCharacters усекается в результирующую строку.  
  
 `pString`  
 [out] Строки BSTR чтение из целевого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает значение S_FALSE, если усечение.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)