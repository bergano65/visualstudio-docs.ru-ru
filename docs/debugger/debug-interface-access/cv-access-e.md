---
title: CV_access_e | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c77135fe5ab8e6971bac7cb17d8fa98e5c20577a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986570"
---
# <a name="cvaccesse"></a>CV_access_e
Задает область видимости (уровень доступа) для функций-членов и переменных.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Элементы  
 CV_private  
 Элемент имеет закрытый доступ.  
  
 CV_protected  
 Член имеет защищенный доступ.  
  
 CV_public  
 Элемент имеет общий доступ.  
  
## <a name="remarks"></a>Примечания  
 `friend` Спецификатор доступа, здесь не так, как они обычно используются не являющиеся членами функции, которые имеют доступ к закрытым и защищенным элементам класса. Используйте [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) поиск символов с помощью метода `SymTagFriend` доступа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также раздел  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)