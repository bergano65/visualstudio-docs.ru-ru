---
title: Преобразование анонимного типа в класс
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e3613f365b2510111f6854087a597df387ab1a4c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335884"
---
# <a name="convert-anonymous-type-to-class"></a>Преобразование анонимного типа в класс

Область применения этого рефакторинга:

- C#

**Что?** Преобразование анонимного типа в класс.

**Когда?** У вас есть анонимный тип, который вы хотите создавать в классе.

**Зачем?** Анонимные типы полезны, если вы используете их только локально. По мере роста вашего кода удобно иметь простой способ переместить их в класс.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в анонимном типе.
2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Преобразование анонимного типа в класс](media/convert-anon-to-class.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Преобразование анонимного типа в класс принято](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
