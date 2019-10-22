---
title: 'Метод метод ijsdebugdatatarget:: Реаднуллтерминатедстринг | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67d6ee6c8dad81865767b0b944ef311fc0de0063
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572398"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>Метод IJsDebugDataTarget::ReadNullTerminatedString
Считывает указанное количество символов из целевого объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 окне Адрес, из которого производится чтение.  
  
 `characterSize`  
 [in] размер каждого символа в строке  
  
 `maxCharacters`  
 окне Максимальное число считываемых символов. Максчарактерс должен быть разумным. Любой запрос на более 128 МБ памяти завершится ошибкой.  Если строка больше Максчарактерс, то после Максчарактерс строка результата будет обрезана.  
  
 `pString`  
 заполняет Значение BSTR, считанное из целевого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Заметки  
 Возвращает значение S_FALSE при усечении.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)