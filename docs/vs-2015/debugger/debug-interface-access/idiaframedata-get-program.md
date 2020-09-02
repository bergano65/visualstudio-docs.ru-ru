---
title: 'IDiaFrameData:: get_program | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d87f5c7fda25a901d44b9f511b9a92eb4471f845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180002"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает строку программы, используемую для расчета набора регистров перед вызовом текущей функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает строку программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Строка программы — это последовательность макросов, интерпретируемая для создания пролога. Например, типичный кадр стека может использовать строку программы `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Формат представляет собой нотацию инвертированного польского языка, где операторы следуют за операндами. `T0` представляет временную переменную в стеке. В этом примере выполняются следующие действия.  
  
1. Переместить содержимое Register `ebp` в `T0` .  
  
2. Добавьте `4` к значению в `T0` для получения адреса, получите значение из этого адреса и сохраните значение в регистре `eip` .  
  
3. Получите значение из адреса, хранящегося в, `T0` и сохраните это значение в регистре `ebp` .  
  
4. Добавьте `8` к значению в `T0` и сохраните это значение в регистре `esp` .  
  
   Обратите внимание, что строка программы зависит от ЦП и от соглашения о вызовах, настроенного для функции, представленной текущим кадром стека.  
  
## <a name="see-also"></a>См. также:  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
