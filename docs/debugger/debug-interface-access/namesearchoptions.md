---
title: "NameSearchOptions | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ceadd085a3099721e73e04dd09ea5a0b81ad1d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="namesearchoptions"></a>NameSearchOptions
Задает параметры поиска для символов и имена файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
enum NameSearchOptions {   
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
 Применяет совпадения имени, без учета регистра.  
  
 `nsfFNameExt`  
 Считает имена путей и применяет имяфайла.расширение совпадения имени.  
  
 `nsfRegularExpression`  
 Применяет соответствия имя с учетом регистра, с помощью звездочки (*) и вопросительные знаки (?) в качестве символов-шаблонов.  
  
 `nsfUndecoratedName`  
 Применяется только к символам, которые внешних и внутренних имен.  
  
## <a name="remarks"></a>Примечания  
 Значения из этого перечисления передаются следующие методы:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)