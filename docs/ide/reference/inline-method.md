---
title: Встроенный метод
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
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403570"
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

    ![Преобразование класса в абстрактный](media/inline-method-remove-declaration.png)

   Выберите **Встроить и сохранить `<QualifiedMethodName>`** , чтобы сохранить исходное объявление метода: 

    ![Преобразование класса в абстрактный](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
