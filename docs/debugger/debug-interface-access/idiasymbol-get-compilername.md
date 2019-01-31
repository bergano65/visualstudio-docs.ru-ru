---
title: IDiaSymbol::get_compilerName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_compilerName method
ms.assetid: 66eaaf72-68d4-40ee-b132-97bea9fe395c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5cd72f9ce9b38d6c349d0c3592dac16eab0344f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031137"
---
# <a name="idiasymbolgetcompilername"></a>IDiaSymbol::get_compilerName
Возвращает имя компилятор, используемый для создания [единице компиляции](../../debugger/debug-interface-access/compiland.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_compilerName (  
   BSTR *pName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pName`  
 Указатель на строку BSTR, который будет содержать имя Юникода компилятора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)