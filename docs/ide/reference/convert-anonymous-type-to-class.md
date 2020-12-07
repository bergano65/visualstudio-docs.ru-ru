---
title: Преобразование анонимного типа в класс
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для преобразования анонимного типа в класс в Visual Studio.
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
monikerRange: '>= vs-2019'
ms.openlocfilehash: a041c077a41ce6b37d74507723ec1ce0f8c9585c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040789"
---
# <a name="convert-anonymous-type-to-class"></a>Преобразование анонимного типа в класс

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Преобразование анонимного типа в класс.

**Когда?** У вас есть анонимный тип, который вы хотите создавать в классе.

**Зачем?** Анонимные типы полезны, если вы используете их только локально. По мере роста вашего кода удобно иметь простой способ переместить их в класс.

## <a name="how-to"></a>Практическое руководство

1. Поместите курсор в анонимном типе.
2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

   ![Преобразование анонимного типа в класс](media/convert-anon-to-class.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

   ![Преобразование анонимного типа в класс принято](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
