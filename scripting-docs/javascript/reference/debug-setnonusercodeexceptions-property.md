---
title: Свойство Debug.setNonUserCodeExceptions | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f53084d5580bc7b6b6c6356268dc60f519b2bd6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636164"
---
# <a name="debugsetnonusercodeexceptions-property"></a>Свойство Debug.setNonUserCodeExceptions
Определяет все блоки try-catch в этой области следует рассматривать как обработанные пользовательским кодом в отладчике. Может быть классифицируются как исключение, обработанное пользовательским кодом или необработанных исключений.  
  
 Если это свойство имеет значение `true` в данной области, отладчик может определить для выполнения некоторых действий (например, прерывание) на исключения, созданные внутри этой области, если разработчик желает прерывание пользовательским кодом исключений. Если это свойство имеет значение `false` будет таким же, как если бы свойство никогда не было задано.  
  
 Дополнительные сведения об отладке см. в разделе [Обзор отладки активных скриптов](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как задать это свойство.  
  
```JavaScript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]