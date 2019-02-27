---
title: Кодируемый URI содержит недопустимый символ | Документация Майкрософт
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
ms.openlocfilehash: a3c71b90d0711bf317d0ed72d51c0d5d45297c80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841874"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Кодируемый URI содержит недопустимый символ
Была предпринята попытка кодирования строки как универсальный код ресурса (URI), но он содержит недопустимые символы. Несмотря на то, что большинство символы допустимы в строках, преобразуемых в URI, некоторые последовательности знаков Юникода не допускаются.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что Кодируемая строка содержит только допустимые последовательности Юникода. Полный код URI состоит из последовательности компонентов и разделителей. Имена в угловых скобках представляют компоненты, а «:», «/», «;» и «?» являются зарезервированными символами, используемыми в качестве разделителей. Выглядит следующим образом:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)