---
title: IDiaSession::findSymbolByVA | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSession::findSymbolByVA method
ms.assetid: 0350df23-9a5d-4e8d-8c26-7f571d8fb1af
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4109d7100f9e2f7e4040ceaba2c93bb04aa59b80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764901"
---
# <a name="idiasessionfindsymbolbyva"></a>IDiaSession::findSymbolByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает тип указанного символа, который содержит, или ближайший к указанному виртуальному адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findSymbolByVA (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Указывает виртуальный адрес.  
  
 `symtag`  
 [in] Найти тип символа. Значения берутся из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления.  
  
 `ppSymbol`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByVA( va, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



