---
title: "Комментарий операторов (JavaScript) | Документы Microsoft"
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
- Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="comment-statements-javascript"></a>Операторы комментария (JavaScript)
Заставляет синтаксический анализатор [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] игнорировать комментарии.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>Примечания  
 Аргумент `comment` представляет собой текст комментария, который требуется добавить в скрипт. Используйте аргумент `condStatement`, если активируется условная компиляция. Если используются однострочные комментарии, пробела между символами // и @ можно не ставить.  
  
 Комментарии позволяют запретить синтаксическому анализатору [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] чтение некоторых частей скрипта. С помощью комментариев можно добавлять пояснения к программному коду.  
  
 Если комментарий однострочный, средство синтаксического анализа пропускает текст от метки комментария до конца строки. В случае многострочных комментариев пропускается текст, расположенный между метками начала и окончания комментария.  
  
 Комментарии обеспечивают поддержку условной компиляции и в то же время сохраняют совместимость с браузерами, которые не поддерживают эту возможность. Такие браузеры обрабатывают подобные формы как комментарии, состоящие из одной или нескольких строк соответственно.  
  
## <a name="example"></a>Пример  
 В следующем примере показаны наиболее распространенные способы применения комментариев.  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать условную компиляцию. В данном примере используются специальные разделители комментариев, которые применяются только тогда, когда условная компиляция активируется с помощью оператора `@cc_on`. Обработчики скриптов, не поддерживающие условную компиляцию, видят только сообщение о том, что условная компиляция не поддерживается.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]