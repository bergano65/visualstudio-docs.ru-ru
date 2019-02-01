---
title: IDiaEnumInjectedSources::Item | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d258e2c1ba71ab294435f2437c7b6dc3de75cfb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925799"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Получает введенный код с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 индекс  
 [in] Индекс [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) извлекаемый объект. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) метод.  
  
 injectedSource  
 [out] Возвращает [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) объект, представляющий введенный код.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)