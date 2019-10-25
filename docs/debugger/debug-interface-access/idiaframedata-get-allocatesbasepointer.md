---
title: 'IDiaFrameData:: get_allocatesBasePointer | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 283ef71b32c186956804cb3afe121af53a99abfc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743643"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Получает флаг, указывающий, выделен ли базовый указатель для кода в этом диапазоне адресов. Этот метод является нерекомендуемым.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает `TRUE`, если базовый указатель выделен; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Это свойство должно использоваться только кодом, который ранее обращался к FPO_DATA, или когда строка программы, возвращаемая методом [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) , `NULL`. В противном случае строка программы содержит все сведения, необходимые для расчета предыдущих значений регистров.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)