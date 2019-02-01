---
title: NameSearchOptions | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bbe801b749b60cd22ce8a980ea78b7713fa4422
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973893"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Указывает параметры поиска для символов и имена файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## <a name="elements"></a>Элементы  
 `nsNone`  
 Параметры не указаны.  
  
 `nsfCaseSensitive`  
 Применяет совпадения имени, с учетом регистра.  
  
 `nsfCaseInsensitive`  
 Применяет совпадение имя без учета регистра.  
  
 `nsfFNameExt`  
 Обрабатывает имена как пути и применяет имяфайла.расширение совпадения имени.  
  
 `nsfRegularExpression`  
 Применяется на совпадение имени с учетом регистра, с помощью звездочки (*) и вопросительные знаки (?) в качестве символов-шаблонов.  
  
 `nsfUndecoratedName`  
 Применяется только к символам, которые внешних и внутренних имен.  
  
## <a name="remarks"></a>Примечания  
 Значения из этого перечисления передаются следующие методы:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
## <a name="see-also"></a>См. также раздел  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)