---
title: "Невозможно присвоить для &#39; это &#39; | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>Невозможно присвоить для &#39; это &#39;
Предпринята попытка присвоить значение **это**. **Это** — [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ключевое слово, которое ссылается один:  
  
-   метод, в данный момент объект  
  
-   глобальный объект, если текущий метод отсутствует (или метод не принадлежит к любой другой объект).  
  
 Метод является [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] функция, вызываемая с помощью объекта. В методе **это** ключевое слово является ссылкой на объект, метод был вызван с помощью (которого происходит этот объект создается посредством вызова конструктора класса с **новый** оператор).  
  
 Внутри метода, можно использовать **это** для ссылки на текущий объект, но нельзя присвоить новое значение для **это**.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Не пытайтесь присвоить **это**. Для доступа к свойству или методу экземпляра объекта, используйте оператор "точка" (например, circle**.** RADIUS).  
  
    > [!NOTE]
    >  Невозможно присвоить имя переменной, созданной пользователем **это**; это [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] зарезервированным словом.  
  
## <a name="see-also"></a>См. также  
 [Эта инструкция](../../javascript/reference/this-statement-javascript.md)   
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)