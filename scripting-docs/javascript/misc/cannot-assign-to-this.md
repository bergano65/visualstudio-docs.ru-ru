---
title: Невозможно присвоить «this» | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f147e591969f803533bb23ff16d73ee9af2c3d27
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839793"
---
# <a name="cannot-assign-to-this"></a>Нельзя назначить this
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