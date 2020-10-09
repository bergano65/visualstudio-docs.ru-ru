---
title: Ожидалось логическое значение | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862660"
---
# <a name="boolean-expected"></a>Требуется логическое значение
Предпринята попытка вызвать метод **Boolean. prototype. ToString** или **Boolean. prototype. valueOf** для объекта типа, отличного от `Boolean` . Объект этого типа вызова должен иметь тип `Boolean` . Пример:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Исправление ошибки

- Вызываются только методы **Boolean. prototype. ToString** или **Boolean. prototype. valueOf** для объектов типа **Boolean.**

## <a name="see-also"></a>См. также

- [Объект Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Типы данных](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Управление выполнением программы](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Копирование, передача и сравнение данных](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)