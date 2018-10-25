---
title: Ожидается логическое значение | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868096"
---
# <a name="boolean-expected"></a>Ожидается логическое значение
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