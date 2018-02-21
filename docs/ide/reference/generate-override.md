---
title: "Создание переопределения метода в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: df0eecdeb2aad15e1da68cef3b125c3c95f57e78
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="generate-an-override-in-visual-studio"></a>Создание переопределения в Visual Studio

Область применения этого формирования кода:

- C#

- Visual Basic

**Что.** Немедленное создание кода для любого метода, который можно переопределить из базового класса.

**Когда.** Необходимо переопределить метод базового класса и автоматически создать сигнатуру.

**Зачем.** Сигнатуру метода можно написать самостоятельно, но эта функция автоматически создает сигнатуру.

## <a name="how-to"></a>Практические советы

1. Введите `override` в C# или `Overrides` в Visual Basic и затем пробел, куда хотите вставить метод для переопределения.

   - C#:

    ![Переопределение IntelliSense в C#](media/override-intellisense-cs.png)

   - Visual Basic:

    ![Переопределение IntelliSense в VB](media/override-intellisense-vb.png)

1. Выберите метод, который требуется переопределить, в базовом классе.

   > [!TIP]
   > - Используйте значок свойства, ![Значок свойства](media/override-property-cs.png) чтобы отобразить или скрыть свойство в списке.
   > - Используйте значок метода, ![Значок метода](media/override-method-cs.png) чтобы отобразить или скрыть метод в списке.

   Выбранный метод или свойство добавляются в класс как переопределение, готовое к реализации.

   - C#:

      ![Результат переопределения в C#](media/override-result-cs.png)

   - Visual Basic:

      ![Результат переопределения в VB](media/override-result-vb.png)

## <a name="see-also"></a>См. также

[Создание кода](../code-generation-in-visual-studio.md)
