---
title: Создание операторов IEquatable для структур
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ccc5be9debbdc2b4901d4aad15a0dc4d2bf1bb9f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290905"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Создание операторов IEquatable при создании Equals для структур

Область применения этого формирования кода:

- C#

**Что?** Позволяет создавать операторы **Equals** и **IEquatable** для [структур](https://docs.microsoft.com/dotnet/csharp/language-reference/builtin-types/struct).

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
