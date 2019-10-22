---
title: Ожидалось логическое значение | Документация Майкрософт
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
ms.openlocfilehash: 91ff0ec8cbd6e5cedb5ec02a8c574ff137b1c6ad
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576060"
---
# <a name="boolean-expected"></a>Требуется логическое значение
Предпринята попытка вызвать метод **Boolean. prototype. ToString** или **Boolean. prototype. valueOf** для объекта типа, отличного от `Boolean`. Объект этого типа вызова должен иметь тип `Boolean`. Пример:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Исправление ошибки

- Вызываются только методы **Boolean. prototype. ToString** или **Boolean. prototype. valueOf** для объектов типа **Boolean.**

## <a name="see-also"></a>См. также

- [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Типы данных](../../javascript/data-types-javascript.md)
- [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)
- [Копирование, передача и сравнение данных](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)