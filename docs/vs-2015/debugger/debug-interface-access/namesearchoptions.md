---
title: NameSearchOptions | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29b6500ab138883c8cbf71eda5a0afad1329494e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979079"
---
# <a name="namesearchoptions"></a>NameSearchOptions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает параметры поиска для символов и имена файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
