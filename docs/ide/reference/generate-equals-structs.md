---
title: Создание операторов IEquatable для структур
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для создания операторов Equals и IEquatable для структур.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05792636e1094c53869f0235145aec73b26deea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952984"
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