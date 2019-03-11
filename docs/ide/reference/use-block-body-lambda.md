---
title: Использование тела лямбда-выражения или блока
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 01ea32ffe978d7b1544597857187f00bec9c3467
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324769"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Использование тела выражения или блока для лямбда-выражений

Область применения этого рефакторинга:

- C#

**Что?** Позволяет выполнить рефакторинг лямбда-выражения для использования тела выражения или блока.

**Когда?** Вы предпочитаете, чтобы в лямбда-выражениях использовалось тело выражения или блока. 

**Зачем?** Можно выполнить рефакторинг лямбда-выражений для повышения удобочитаемости в соответствии с предпочтениями пользователя.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Рефакторинг тела выражения или блока для лямбда-выражений

1. Поместите курсор справа от лямбда-оператора.
2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

  ![Использование тела лямбда-выражения или блока](media/block-body-lambda.png)

3. Выберите **Использовать тело блока для лямбда-выражений** или **Использовать тело выражения для лямбда-выражений**.

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)