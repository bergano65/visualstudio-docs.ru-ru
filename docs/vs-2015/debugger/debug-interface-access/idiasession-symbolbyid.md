---
title: IDiaSession::symbolById | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac409edcee7657e724822d1a72737c3142d8d93e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979757"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает символ по его уникальному идентификатору.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Указанный идентификатор является внутренним классом DIA SDK чтобы сделать все символы уникальным уникальное значение.  
  
 Этот метод может использоваться, например, для получения символ, представляющий тип другого символа (см. пример).  
  
## <a name="example"></a>Пример  
 В этом примере извлекаются [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) представляющий от другого типа. В этом примере показано, как использовать `symbolById` метод в сеансе. Более простой подход является вызов [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) метод для извлечения типа символа напрямую.  
  
```cpp#  
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
