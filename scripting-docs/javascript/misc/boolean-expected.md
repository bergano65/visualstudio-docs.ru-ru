---
title: Ожидается логическое значение | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
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
ms.openlocfilehash: 82123fe2a38b3de1d6e6c015f47bc5f7edd02791
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840528"
---
# <a name="boolean-expected"></a>Требуется логическое значение
Предпринята попытка вызова **Boolean.prototype.toString** или **Boolean.prototype.valueOf** метод на объект типа, отличных от `Boolean`. Объект этого типа вызова должен иметь тип `Boolean`. Пример:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Исправление ошибки

- Вызывается только **Boolean.prototype.toString** или **Boolean.prototype.valueOf** методов в объектах типа **логическое.**

## <a name="see-also"></a>См. также

- [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Типы данных](../../javascript/data-types-javascript.md)
- [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)
- [Копирование, передача и сравнение данных](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)