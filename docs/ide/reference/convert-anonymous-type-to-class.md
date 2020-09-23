---
title: Преобразование анонимного типа в класс
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 251a011695f6f5056e1fdf8e1a6be36b898b66f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809215"
---
# <a name="convert-anonymous-type-to-class"></a>Преобразование анонимного типа в класс

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Преобразование анонимного типа в класс.

**Когда?** У вас есть анонимный тип, который вы хотите создавать в классе.

**Зачем?** Анонимные типы полезны, если вы используете их только локально. По мере роста вашего кода удобно иметь простой способ переместить их в класс.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в анонимном типе.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Преобразование анонимного типа в класс](media/convert-anon-to-class.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Преобразование анонимного типа в класс принято](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
