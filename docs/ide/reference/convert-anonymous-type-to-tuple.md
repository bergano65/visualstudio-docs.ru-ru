---
title: Преобразование анонимного типа в кортеж
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f7e89c5b5a05900fe42af62ef87f70292e94e662
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094279"
---
# <a name="convert-anonymous-type-to-tuple"></a>Преобразование анонимного типа в кортеж

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Преобразование анонимного типа в кортеж.

**Когда?** У вас есть анонимный тип, который является кортежем.

**Зачем?** [Кортежи](/dotnet/csharp/tuples) могут быть полезны для упрощения синтаксиса. Это быстрое действие позволяет с удобством воспользоваться этой возможностью C#.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в анонимном типе.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Преобразование анонимного типа в кортеж](media/convert-anon-to-tuple.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Преобразование анонимного типа в кортеж](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
