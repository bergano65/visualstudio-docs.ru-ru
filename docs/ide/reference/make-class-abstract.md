---
title: Преобразование класса в абстрактный
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
ms.openlocfilehash: 8bfcaa7117249ceffbaed706ac420c5250c02089
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403578"
---
# <a name="make-class-abstract"></a>Преобразование класса в абстрактный

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Рефакторинг "Преобразование класса в абстрактный".

**Когда?** Написание абстрактного метода в классе, который не является абстрактным.

**Зачем?**  Наличие исправления кода, позволяющего преобразовать класс в абстрактный после написания абстрактного метода, позволит сэкономить время.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в абстрактный метод.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

3. Выберите **Make class "abstract"** (Сделать класс абстрактным).

    ![Преобразование класса в абстрактный](media/make-class-abstract.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
