---
title: IDiaSymbol::getSrcLineOnTypeDefn | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2112f7186ee8bb861cf4d283b0bb0b4499f2c4ae
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023997"
---
# <a name="idiasymbolgetsrclineontypedefn"></a>IDiaSymbol::getSrcLineOnTypeDefn
Извлекает исходный файл и номер строки, указывающие, где определен указанного определяемого пользователем типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT getSrcLineOnTypeDefn(  
   IDiaLineNumber **ppResult);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppResult`  
 [out] Объект `IDiaLineNumber` , содержащий исходный файл и номер строки, где определяются пользователем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)