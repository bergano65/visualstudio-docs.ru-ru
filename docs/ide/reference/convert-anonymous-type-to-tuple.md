---
title: Преобразование анонимного типа в кортеж
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335875"
---
# <a name="convert-anonymous-type-to-tuple"></a>Преобразование анонимного типа в кортеж

Область применения этого рефакторинга:

- C#

**Что?** Преобразование анонимного типа в кортеж.

**Когда?** У вас есть анонимный тип, который является кортежем.

**Зачем?** [Кортежи](/dotnet/csharp/tuples) могут быть полезны для упрощения синтаксиса. Это быстрое действие позволяет с удобством воспользоваться этой возможностью C#.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в анонимном типе.
2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Преобразование анонимного типа в кортеж](media/convert-anon-to-tuple.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Преобразование анонимного типа в кортеж](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
