---
title: Преобразование typeof в nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400328"
---
# <a name="convert-typeof-to-nameof"></a>Преобразование `typeof` в `nameof`

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Позволяет преобразовать экземпляр `typeof(<QualifiedType>).Name` в `nameof(<QualifiedType>)` в C# и экземпляр `GetType(<QualifiedType>).Name` в `NameOf(<QualifiedType>)` в Visual Basic.

**Когда?**  Все экземпляры `typeof(<QualifiedType>).Name`, где `someType` не является универсальным типом. Это исключение необходимо, так как в этом случае не возвращается то же строковое значение, что и `nameof(<QualifiedType>)`. Это справедливо и для экземпляра Visual Basic.

**Зачем?** Использование `nameof` вместо имени `type` позволяет избежать отражения, связанного с получением объекта `type`, и является более практичным способом его написания.

## <a name="how-to"></a>Практическое руководство

1. Поместите курсор в экземпляр `typeof(<QualifiedType>).Name` для C# или в `GetType(<QualifiedType>).Name` для Visual Basic.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

3. Выберите один из следующих вариантов:

    - C#
      <br>Выберите **Преобразовать typeof в nameof**: ![Преобразование typeof в nameof](media/convert-type-of.PNG)

    - Visual Basic
      <br>Выберите **Преобразовать GetType в NameOf**: ![Преобразование typeof в nameof](media/convert-get-type.PNG)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
