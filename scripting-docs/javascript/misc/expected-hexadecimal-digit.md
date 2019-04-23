---
title: Ожидаемый шестнадцатеричная цифра | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c2507acd42336511dadc3dedd2eba15fe0d5b76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050079"
---
# <a name="expected-hexadecimal-digit"></a>Ожидалась шестнадцатеричная цифра
Вы создали неверные escape-последовательности Юникода. Escape-последовательности Юникода начинаются с \u, следуют ровно четыре шестнадцатеричные цифры (не больше и не меньше). Шестнадцатеричные цифры в Юникоде может содержать только цифры 0 – 9, прописные буквы A-F и строчные буквы a-f. Ниже приведен пример неправильно сформирован escape-последовательность Юникода.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что ваш шестнадцатеричных цифр Юникода начинаются с \u, содержит только цифры 0 – 9, прописные буквы A-F, строчные буквы a – f; которые сгруппированы в четыре цифры.  
  
    > [!NOTE]
    >  Если вы хотите использовать \u литеральный текст в строке, а затем укажите две черты подряд - (\\\u) — один для первого.  
  
## <a name="see-also"></a>См. также  
 [Типы данных](../../javascript/data-types-javascript.md)