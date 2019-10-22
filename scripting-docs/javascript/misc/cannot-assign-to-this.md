---
title: Невозможно присвоить значение "this" | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
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
ms.openlocfilehash: 73baa77cc63e3a43ac30e70f66081bbc7ade3020
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572348"
---
# <a name="cannot-assign-to-this"></a>Нельзя назначить this
Предпринята попытка присвоить значение **этому**. **это** [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ключевое слово, которое ссылается на один из следующих способов:

- Объект, выполняющий в данный момент метод,

- глобальный объект, если текущий метод отсутствует (или метод не принадлежит какому-либо другому объекту).

Метод — это [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] функция, которая вызывается через объект. Внутри метода ключевое слово **this** является ссылкой на объект, с помощью которого был вызван метод (который, как это происходит, является объектом, созданным путем вызова конструктора класса с помощью оператора **New** ).

Внутри метода **это** можно использовать для ссылки на текущий объект, но нельзя присвоить ему новое **значение.**

## <a name="to-correct-this-error"></a>Исправление ошибки

- Не пытайтесь присвоить **этому**. Чтобы получить доступ к свойству или методу экземпляра объекта, используйте оператор "точка" (например, **Circle. RADIUS**).

  > [!NOTE]
  > Вы не можете присвоить имя созданной **пользователем переменной.** Это [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] зарезервированное слово.

## <a name="see-also"></a>См. также

- [Оператор this](../../javascript/reference/this-statement-javascript.md)
- [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)