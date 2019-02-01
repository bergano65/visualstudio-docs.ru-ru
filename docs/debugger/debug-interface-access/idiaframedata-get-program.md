---
title: IDiaFrameData::get_program | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f356dec92e1553eba0b8704f6d456b4d1fb4326f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916346"
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Извлекает строку программы, которая используется для вычисления регистра задать перед вызовом текущей функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает строку программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Строка программы — это последовательность макросов, который интерпретируется для того чтобы установить пролога. Например, кадр стека типичный может использовать строку программы `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Формат — обратная польская нотация, где операторы следуют операндов. `T0` Представляет временной переменной в стеке. Этот пример выполняет следующие действия:  
  
1. Переместить содержимое регистра `ebp` для `T0`.  
  
2. Добавить `4` значению `T0` для создания адреса, извлекать пользу из этого адреса и сохраните значение в регистре `eip`.  
  
3. Получить значение из адреса, хранящегося в `T0` и сохраняет введенное число в регистре `ebp`.  
  
4. Добавить `8` значению `T0` и сохраняет введенное число в регистре `esp`.  
  
   Обратите внимание, что строка программы относится к ЦП и соглашение о вызовах для функции, представленной текущим кадром стека.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)