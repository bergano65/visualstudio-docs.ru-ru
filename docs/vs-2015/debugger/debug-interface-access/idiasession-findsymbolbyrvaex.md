---
title: IDiaSession::findSymbolByRVAEx | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f9c938439fde85104b5206430c8d7b4f991a067
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559269"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSession::findSymbolByRVAEx](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findsymbolbyrvaex).  
  
Возвращает тип указанного символа, который содержит, или ближайший к указанным относительный виртуальный адрес (RVA) и смещение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rva`  
 [in] Указывает RVA.  
  
 `symtag`  
 [in] Найти тип символа. Значения берутся из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления.  
  
 `ppSymbol`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.  
  
 `displacement`  
 [out] Возвращает значение, указывающее смещение относительно относительный виртуальный адрес, указанный в `rva`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



