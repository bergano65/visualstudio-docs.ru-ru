---
title: IDiaSymbol::get_lexicalParentId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lexicalParentId method
ms.assetid: 6c0c2874-cc47-4e4f-ad9c-02a18a108d9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb3d8b21c938c090b7e568e5accaa3fa2087518b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987392"
---
# <a name="idiasymbolgetlexicalparentid"></a>IDiaSymbol::get_lexicalParentId
Получает идентификатор лексической родительского символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_lexicalParentId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает идентификатор лексической родительского символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор — это уникальное значение, созданные с помощью пакета SDK доступа к интерфейсу отладки, чтобы пометить все символы как уникальный.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)