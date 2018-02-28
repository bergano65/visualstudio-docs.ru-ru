---
title: "IDiaSession::symbolById | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c6792f3271f09742d40b92691dee06854deea8f2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Возвращает символ, его уникальный идентификатор.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 [in] Уникальный идентификатор.  
  
 `ppSymbol`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Указанный идентификатор — это уникальное значение, которые используются внутренним образом пакет SDK для чтобы сделать уникальным все символы.  
  
 Этот метод может использоваться, например, для получения символ, представляющий тип символа другим (см. пример).  
  
## <a name="example"></a>Пример  
 В этом примере извлекается [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) отражающее тип проверяемых другой символ. В этом примере показано, как использовать `symbolById` метода в сеансе. Более простой подход — вызов [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) метод для извлечения символ типа напрямую.  
  
```C++  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)