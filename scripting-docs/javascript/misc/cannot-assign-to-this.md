---
title: Невозможно присвоить «this» | Документация Майкрософт
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
ms.openlocfilehash: 4a4ba5d852a7d131a88930dd66931c026074549b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149501"
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