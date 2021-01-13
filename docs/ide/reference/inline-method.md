---
title: Встроенный метод
description: Сведения об использовании меню Quick Actions and Refactorings (Быстрые действия и рефакторинг) в Visual Studio для выполнения рефакторинга объявлений встроенного метода и предоставления более понятного синтаксиса.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761424"
---
# <a name="inline-method"></a>Встроенный метод

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Рефакторинг для встраивания метода. 

**Когда?** Требуется заменить использование статических методов, экземпляров и расширений в пределах тела одного оператора с возможностью удаления исходного объявления метода.

**Зачем?**  Этот рефакторинг предоставит более четкий синтаксис.

## <a name="how-to"></a>Практические советы

1. Наведите курсор на место использования метода.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

3. Выберите один из следующих вариантов: 
    
   Выберите **Встроить `<QualifiedMethodName>`** , чтобы удалить объявление встраиваемого метода: 

    ![Снимок экрана: меню Quick Actions and Refactorings (Быстрые действия и рефакторинг) в Visual Studio, в котором выбран параметр "Преобразовать "Inline CreateWidget()" и показаны изменения кода C#.](media/inline-method-remove-declaration.png)

   Выберите **Встроить и сохранить `<QualifiedMethodName>`** , чтобы сохранить исходное объявление метода: 

    ![Снимок экрана: меню Quick Actions and Refactorings (Быстрые действия и рефакторинг) в Visual Studio, в котором все еще выбран параметр "Преобразовать "Inline CreateWidget()" и показаны изменения кода C#.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
