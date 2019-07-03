---
title: Создание параметра с использованием рефакторинга
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329068"
---
# <a name="generate-parameter"></a>Создание параметра

Область применения этого рефакторинга:

- C#

**Что?** Автоматически создает параметр метода.

**Когда?** Если вы ссылаетесь на переменную в методе, который не существует в текущем контексте, и получаете сообщение об ошибке, вы можете создать параметр в качестве исправления кода. 

**Зачем?** Вы можете быстро изменить сигнатуру метода, не теряя контекст.

## <a name="how-to"></a>Практические советы

1. Поместите курсор в имя переменной и нажмите клавиши **Ctrl**+ **.** , чтобы открыть меню **Быстрые действия и рефакторинг**.
1. Выберите **Создать параметр**.

   ![Создание параметра](media/generate-parameter.png) 

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
