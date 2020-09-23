---
title: Создание операторов IEquatable для структур
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5ee695169f52036858fc70598f81f375638ab03f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808120"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Создание операторов IEquatable при создании Equals для структур

Область применения этого формирования кода:

- C#

**Что?** Позволяет создавать операторы **Equals** и **IEquatable** для [структур](/dotnet/csharp/language-reference/builtin-types/struct).

**Когда?** Если у вас есть структура, IEquatable и операторы равенства и неравенства будут добавлены автоматически.

**Зачем?**

- Если вы реализуете тип значения, рекомендуем переопределить метод **Equals**, чтобы повысить производительность по сравнению со стандартной реализацией метода Equals в ValueType.

- Реализация интерфейса IEquatable реализует зависящий от типа метод Equals().

## <a name="how-to"></a>Практические советы

1. Поместите курсор в любую позицию на строке объявления структуры.

2. Затем выполните одно из следующих действий:

   - Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   - Щелкните правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**.

   - Нажмите кнопку ![с отверткой](../media/screwdriver-icon.png) , которая отображается в левом поле.

   ![Создание IEquatable и Equals для структур](media/generate-equals-structs.png)

3. В раскрывающемся меню выберите **Создать "Equals(object)"** .

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)