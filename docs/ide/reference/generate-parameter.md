---
title: Создание параметра с использованием рефакторинга
description: Узнайте, как использовать меню "Быстрые действия и рефакторинг" для автоматического создания параметра метода.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 33e2be19e3a5a83d89e722aa0c1a1154c8196939
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968038"
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
