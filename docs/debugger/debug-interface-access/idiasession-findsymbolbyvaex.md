---
title: IDiaSession::findSymbolByVAEx | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d645905a98bd512f70583f6bc236730028ab343
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026795"
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
Возвращает тип указанного символа, который содержит, или ближайший к указанному виртуальному адресу (VA) и смещение.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Указывает ва.  
  
 `symtag`  
 [in] Найти тип символа. Значения берутся из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления.  
  
 `ppSymbol`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.  
  
 `displacement`  
 [out] Возвращает значение, указывающее смещение относительно виртуального адреса, заданного выражением `va`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
  
```C++  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)