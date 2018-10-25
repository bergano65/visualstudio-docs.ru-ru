---
title: Невозможно присвоить &#39;это&#39; | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47e55d39e85675b37d2ac9741d1207a9e81d369e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856656"
---
# <a name="cannot-assign-to-39this39"></a>Невозможно присвоить &#39;это&#39;
Предпринята попытка присвоить значение **это**. **Это** является [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ключевое слово, которое ссылается один:

- Объект, в настоящее время выполнения метода,

- глобальный объект, если нет текущего метода (или метод не принадлежит к любому другому объекту).

Метод является [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] функция, которая вызывается с помощью объекта. В методе **это** ключевое слово является ссылкой на объект, метод был вызван с помощью (который может быть объект, созданный путем вызова конструктора класса с **новый** оператор).

В методе можно использовать **это** для ссылки на текущий объект, но нельзя присвоить новое значение для **это**.

## <a name="to-correct-this-error"></a>Исправление ошибки

- Не пытайтесь присвоить **это**. Чтобы получить доступ к свойству или методу экземпляра объекта, используйте оператор "точка" (например, **circle.radius**).

  > [!NOTE]
  > Не удается присвоить имя переменной, созданной пользователем **это**; это [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] зарезервированное слово.

## <a name="see-also"></a>См. также

- [Оператор this](../../javascript/reference/this-statement-javascript.md)
- [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)