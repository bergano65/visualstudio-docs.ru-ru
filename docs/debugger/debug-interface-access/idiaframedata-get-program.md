---
title: IDiaFrameData::get_program | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c78c6f1c2c6e8368efd86dc3ffa03a021e46da3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Извлекает строку программы, которая используется для вычисления перед обращением к текущей функции набор регистров.  
  
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
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Строка программы является последовательность макросы, интерпретируются для установления пролога. Например, кадр стека обычно может использовать строку программы `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Формат — польский обратную нотацию, где операторы следуют операндов. `T0` Представляет временной переменной в стеке. В этом примере выполняет следующие действия:  
  
1.  Переместить содержимое регистра `ebp` для `T0`.  
  
2.  Добавить `4` значению в `T0` для получения адреса, получить значение из этого адреса и сохранение значения в регистре `eip`.  
  
3.  Получить значение из адреса, хранящегося в `T0` и сохранить в регистре `ebp`.  
  
4.  Добавить `8` значению в `T0` и сохранить в регистре `esp`.  
  
 Обратите внимание, что программа строка относится к ЦП и соглашение о вызовах для функции, представленный текущим кадром стека.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)