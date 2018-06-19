---
title: Оператор WITH (JavaScript) | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641214"
---
# <a name="with-statement-javascript"></a>Оператор with (JavaScript)
Устанавливает объект по умолчанию для оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Параметры  
 `object`  
 Объект по умолчанию.  
  
 `statements`  
 Один или несколько операторов, для которых `object` является объектом по умолчанию.  
  
## <a name="remarks"></a>Примечания  
 Для сокращения объема кода, который необходимо написать в некоторых случаях, обычно используется оператор `with`.  
  
> [!WARNING]
>  Использование `with` в строгом режиме не допускается. Оператор `with` может усложнить чтение и отладку кода, поэтому обычно следует избегать его использования.  
  
## <a name="example"></a>Пример  
 В следующем примере объект `Math` используется несколько раз.  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Пример  
 Если переписать этот пример с использованием оператора `with`, код будет короче.  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Оператор this](../../javascript/reference/this-statement-javascript.md)