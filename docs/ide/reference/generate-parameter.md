---
title: Создание параметра с использованием рефакторинга
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
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094343"
---
# <a name="generate-parameter"></a>Создание параметра

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Автоматически создает параметр метода.

**Когда?** Если вы ссылаетесь на переменную в методе, который не существует в текущем контексте, и получаете сообщение об ошибке, вы можете создать параметр в качестве исправления кода. 

**Зачем?** Вы можете быстро изменить сигнатуру метода, не теряя контекст.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в имя переменной и нажмите клавиши **Ctrl**+ **.** , чтобы открыть меню **Быстрые действия и рефакторинг**.
1. Выберите **Создать параметр**.

   ![Создание параметра](media/generate-parameter.png) 

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
