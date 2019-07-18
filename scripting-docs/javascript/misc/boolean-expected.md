---
title: Ожидается логическое значение | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
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
ms.openlocfilehash: 261cf0ad93208c0eac09e42dcd68853352318e88
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817904"
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