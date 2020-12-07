---
title: Преобразование анонимного типа в кортеж
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для преобразования анонимного типа в кортеж в Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 452ba826a2765ef624e6c3d04bb20915a26c51fb
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040866"
---
# <a name="convert-anonymous-type-to-tuple"></a>Преобразование анонимного типа в кортеж

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Преобразование анонимного типа в кортеж.

**Когда?** У вас есть анонимный тип, который является кортежем.

**Зачем?** [Кортежи](/dotnet/csharp/tuples) могут быть полезны для упрощения синтаксиса. Это быстрое действие позволяет с удобством воспользоваться этой возможностью C#.

## <a name="how-to"></a>Практическое руководство

1. Поместите курсор в анонимном типе.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Преобразование анонимного типа в кортеж](media/convert-anon-to-tuple.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Преобразование анонимного типа в принятый кортеж](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
