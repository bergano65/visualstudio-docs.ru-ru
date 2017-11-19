---
title: "IDiaSymbol::getSrcLineOnTypeDefn | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0627d02c41fb1564037c56725d3ba26e9ffa2cfe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetsrclineontypedefn"></a>IDiaSymbol::getSrcLineOnTypeDefn
Извлекает исходного файла и номер строки, указывающие, где определен указанного определяемого пользователем типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT getSrcLineOnTypeDefn(  
   IDiaLineNumber **ppResult);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppResult`  
 [out] Объект `IDiaLineNumber` , содержащий исходный файл и номер строки, где определяемой пользователем.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)