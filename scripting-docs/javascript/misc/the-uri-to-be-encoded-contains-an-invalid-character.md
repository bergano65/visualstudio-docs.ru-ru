---
title: URI для кодирования содержит недопустимый символ | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72fd550e27e64754fe8c4857e9aa4d25ae5711a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572248"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Кодируемый URI содержит недопустимый символ
Предпринята попытка кодирования строки в виде универсального кода ресурса (URI), но она содержала недопустимые символы. Хотя большинство символов допустимо в строках для преобразования в URI, некоторые последовательности символов Юникода являются недопустимыми.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что строка, которая должна быть закодирована, содержит только допустимые последовательности Юникода. Полный URI состоит из последовательности компонентов и разделителей. Имена в угловых скобках представляют компоненты, а ":", "/", ";" и "?" являются зарезервированными символами, используемыми в качестве разделителей. Общая форма:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>См. также  
   [функции encodeURI](../../javascript/reference/encodeuri-function-javascript.md)  
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)