---
title: "Метод getVarDate (Date) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>Метод getVarDate (Date) (JavaScript)
Возвращает значение VT_DATE из объекта `Date` .  
  
> [!WARNING]
>  Этот метод поддерживается только в Internet Explorer.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Параметры  
 Обязательная ссылка `dateObj` — это объект `Date` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение VT_DATE.  
  
## <a name="remarks"></a>Примечания  
 Метод `getVarDate` используется, когда код JavaScript взаимодействует с объектами COM, объектами ActiveX и другими объектами, которые принимают и возвращают значения даты в формате VT_DATE. Сюда входят объекты в Visual Basic и Visual Basic Scripting Edition (VBScript). Фактический формат возвращаемого значения зависит от региональных параметров.  
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
 **Применимо к**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Метод getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Функция Date.parse](../../javascript/reference/date-parse-function-javascript.md)