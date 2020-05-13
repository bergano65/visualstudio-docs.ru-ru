---
title: Преобразование между автосвойством и полным свойством
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395739"
---
# <a name="convert-between-auto-property-and-full-property"></a>Преобразование между автосвойством и полным свойством

Область применения этого рефакторинга:

- C#

**Что?** Преобразование автоматически реализуемого свойства в полное свойство.

**Когда?** При изменении логики свойства.

**Зачем?** Преобразовать автоматически реализуемое свойство в полное свойство можно вручную, но эта функция сделает это автоматически. 

## <a name="how-to"></a>Практические советы

1. Поместите курсор на имя свойства.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.
3. Выберите один из следующих двух параметров: 

    Выберите **Преобразовать в полное свойство**.

   ![Преобразование автосвойства в полное свойство](media/convert-auto-property-to-full-property.png) 

    Выберите **Использовать автосвойство**. 

    ![Преобразование полного свойства в автосвойство](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
