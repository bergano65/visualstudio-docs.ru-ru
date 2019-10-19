---
title: URI для декодирования не является допустимой кодировкой | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99df8739137971e32c14f265460ff3f4a9c03816
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572264"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Декодируемый URI закодирован неправильно
Предпринята попытка декодировать URI с неправильным форматом (универсальный идентификатор ресурса). URI имеют специальный синтаксис; Большинство символов, отличных от буквенно-цифровых, должны быть закодированы, прежде чем их можно будет использовать в URI. Для создания URI из обычной [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строки можно использовать методы `encodeURI` и `encodeURIComponent`.  
  
 Полный URI состоит из последовательности компонентов и разделителей. Общая форма:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Имена в угловых скобках представляют компоненты, а ":", "/", ";" и "?" являются зарезервированными символами, используемыми в качестве разделителей.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что вы пытаетесь декодировать только допустимые URI. Нельзя декодировать обычные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строки, так как они могут содержать недопустимые символы.  
  
## <a name="see-also"></a>См. также  
   [функции decodeURI](../../javascript/reference/decodeuri-function-javascript.md)  
 [Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)