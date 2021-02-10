---
title: Преобразование класса в абстрактный
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7b44c8331c10bc0cf2f87e19094a77c0cbec251a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919422"
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
