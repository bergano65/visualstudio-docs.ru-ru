---
title: Преобразование typeof в nameof
description: Сведения об использовании меню Quick Actions and Refactorings (Быстрые действия и рефакторинг) в Visual Studio для преобразования typeof в nameof для C# и преобразования GetType в NameOf для Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919691"
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
      <br>Выберите **Преобразовать typeof в nameof**: ![Снимок экрана: меню Quick Actions and Refactorings (Быстрые действия и рефакторинг) в Visual Studio, в котором выбран параметр "Преобразовать "typeof" в "nameof" и показаны изменения кода C#.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Выберите **Преобразовать GetType в NameOf**: ![Снимок экрана: меню Quick Actions and Refactorings (Быстрые действия и рефакторинг) в Visual Studio, в которм выбран параметр "Преобразовать 'GetType' в 'NameOf'" и показаны изменения кода Visual Basic.](media/convert-get-type.PNG)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
