---
title: IDiaSymbol::get_hasSecurityChecks | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d0ba261429710a71aa87405e9b6dca8bd7704d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924486"
---
# <a name="idiasymbolgethassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Получает флаг, указывающий ли в единице компиляции или функцию был скомпилирован с помощью проверок безопасности на переполнение буфера (например, [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check) переключатель компилятора).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_hasSecurityChecks(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Возвращает `TRUE` Если функция имеет проверок безопасности; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check)