---
title: 'IDiaFrameData:: get_program | Документация Майкрософт'
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
ms.openlocfilehash: 135f2b0a042dd74b573a0746831a48fb27e7c2a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743519"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Возвращает строку программы, используемую для расчета набора регистров перед вызовом текущей функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает строку программы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Строка программы — это последовательность макросов, интерпретируемая для создания пролога. Например, типичный кадр стека может использовать программную строку `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Формат представляет собой нотацию инвертированного польского языка, где операторы следуют за операндами. `T0` представляет временную переменную в стеке. В этом примере выполняются следующие действия.

1. Переместить содержимое `ebp` Register в `T0`.

2. Добавьте `4` значение в `T0` для получения адреса, получите значение из этого адреса и сохраните значение в регистре `eip`.

3. Получите значение из адреса, хранящегося в `T0`, и сохраните это значение в `ebp` Register.

4. Добавьте `8` к значению в `T0` и сохраните это значение в `esp` Register.

   Обратите внимание, что строка программы зависит от ЦП и от соглашения о вызовах, настроенного для функции, представленной текущим кадром стека.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)