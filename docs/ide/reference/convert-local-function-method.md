---
title: Преобразование локальной функции в метод
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96064b16e53081e0456ed43275acd5edf7ead468
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152958"
---
# <a name="convert-local-function-to-method"></a>Преобразование локальной функции в метод

Область применения этого рефакторинга:

- C#
- Visual Basic

**Что?** Преобразование локальной функции в метод

**Когда?** У вас есть локальная функция, которую вы хотите определить за пределами текущего локального контекста.

**Зачем?** Вы можете преобразовать локальную функцию в метод, чтобы ее можно вызвать вне локального контекста. Вы можете выполнить преобразование в метод, если локальная функция становится слишком длинной. Если вы определите ее в отдельный метод, код будет более удобным для чтения.

## <a name="convert-local-function-to-method-refactoring"></a>Рефакторинг "Преобразование локальной функции в метод"

1. Поместите курсор в локальную функцию.

    ![Преобразование локальной функции в метод](media/convert-local-function-to-method.png)

2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Исправление "Преобразование локальной функции в метод"](media/convert-local-function-to-method-codefix.png)

2. Нажмите клавишу **ВВОД**, чтобы принять рефакторинг.

    ![Результат преобразования локальной функции в метод](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
