---
title: Точность выходит за пределы диапазона | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73fb9c7fb35aa33214806ac1d89f4c3f1b9a479e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347077"
---
# <a name="the-precision-is-out-of-range"></a>Точность вне диапазона
Была предпринята попытка передать недопустимый аргумент в функцию **Number.prototype.toPrecision**. Аргумент **toPrecision** должен быть от 1 до 21 (включительно).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Аргумент для `toPrecision` не слишком велико или слишком мало.  
  
## <a name="see-also"></a>См. также  
 [Метод toPrecision (Number)](../../javascript/reference/toprecision-method-number-javascript.md)