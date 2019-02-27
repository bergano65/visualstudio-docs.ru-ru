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
ms.openlocfilehash: e5cf7d77853cb200afe568656e1055459acad7d1
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842303"
---
# <a name="expected-hexadecimal-digit"></a>Ожидалась шестнадцатеричная цифра
Вы создали неверные escape-последовательности Юникода. Escape-последовательности Юникода начинаются с \u, следуют ровно четыре шестнадцатеричные цифры (не больше и не меньше). Шестнадцатеричные цифры в Юникоде может содержать только цифры 0 – 9, прописные буквы A-F и строчные буквы a-f. Ниже приведен пример неправильно сформирован escape-последовательность Юникода.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что ваш шестнадцатеричных цифр Юникода начинаются с \u, содержит только цифры 0 – 9, прописные буквы A-F, строчные буквы a – f; которые сгруппированы в четыре цифры.  
  
    > [!NOTE]
    >  Если вы хотите использовать \u литеральный текст в строке, а затем укажите две черты подряд - (\\\u) — один для первого.  
  
## <a name="see-also"></a>См. также  
 [Типы данных](../../javascript/data-types-javascript.md)