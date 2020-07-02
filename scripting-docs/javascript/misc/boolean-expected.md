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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817675"
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

- [Объект Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Типы данных](../../javascript/data-types-javascript.md)
- [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)
- [Копирование, передача и сравнение данных](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)