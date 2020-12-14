---
title: Создание параметра с использованием рефакторинга
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для автоматического создания параметра метода.
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
ms.openlocfilehash: 21e209f5be9072390df58e78db34811f886fa9c5
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617153"
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

## <a name="see-also"></a>См. также раздел

- [Рефакторинг](../refactoring-in-visual-studio.md)
