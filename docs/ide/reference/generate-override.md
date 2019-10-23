---
title: Создание переопределения метода
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 075c7dc49ffba1d67bbb5b62d313f50b5d09e956
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668435"
---
# <a name="generate-an-override-in-visual-studio"></a>Создание переопределения в Visual Studio

Область применения этого формирования кода:

- C#

- Visual Basic

**Что?** Немедленное создание кода для любого метода, который можно переопределить из базового класса.

**Когда?** Необходимо переопределить метод базового класса и автоматически создать сигнатуру.

**Зачем?** Сигнатуру метода можно написать самостоятельно, но эта функция автоматически создает сигнатуру.

## <a name="how-to"></a>Практические советы

1. Введите `override` в C# или `Overrides` в Visual Basic и затем пробел, куда хотите вставить метод для переопределения.

   - C#:

      ![Переопределение IntelliSense в C#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Переопределение IntelliSense в VB](media/override-intellisense-vb.png)

2. Выберите метод, который требуется переопределить, в базовом классе.

   > [!TIP]
   > - Используйте значок свойства, ![Значок свойства](media/override-property-cs.png) чтобы отобразить или скрыть свойство в списке.
   > - Используйте значок метода, ![Значок метода](media/override-method-cs.png) чтобы отобразить или скрыть метод в списке.

   Выбранный метод или свойство добавляются в класс как переопределение, готовое к реализации.

   - C#:

       ![Результат переопределения в C#](media/override-result-cs.png)

   - Visual Basic:

       ![Результат переопределения в VB](media/override-result-vb.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)