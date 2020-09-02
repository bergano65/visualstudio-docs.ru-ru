---
title: CV_access_e | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164384"
---
# <a name="cv_access_e"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает область видимости (уровень доступа) функций и переменных-членов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Элементы  
 CV_private  
 Член имеет закрытый доступ.  
  
 CV_protected  
 Член имеет защищенный доступ.  
  
 CV_public  
 Член имеет открытый доступ.  
  
## <a name="remarks"></a>Remarks  
 `friend`Спецификатор доступа не указан здесь, так как обычно используется функциями, не являющимися членами, которые имеют доступ как к частным, так и к защищенным элементам класса. Используйте метод [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) , чтобы найти символы с `SymTagFriend` доступом.  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol:: get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
