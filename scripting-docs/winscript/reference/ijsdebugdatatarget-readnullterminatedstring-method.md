---
title: Метод IJsDebugDataTarget::ReadNullTerminatedString | Документация Майкрософт
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
ms.openlocfilehash: 178a2d3705e4904de9253c02319f6ba94e567d76
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146660"
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
 [in] Адрес для чтения из.  
  
 `characterSize`  
 [in] размер каждого символа в строке  
  
 `maxCharacters`  
 [in] Максимальное количество символов для чтения. maxCharacters должно быть разумным. Любой запрос, для более чем 128 МБ памяти завершится ошибкой.  Если строки больше maxCharacters, результирующая строка усекается после maxCharacters.  
  
 `pString`  
 [out] BSTR чтения из целевого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Возвращает значение S_FALSE, если усечено.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)