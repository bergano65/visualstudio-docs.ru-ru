---
title: Добавление атрибута DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290921"
---
# <a name="add-debuggerdisplay-attribute"></a>Добавление атрибута DebuggerDisplay

Область применения этого формирования кода:

- C#

**Что?** [Атрибут DebuggerDisplay](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute) управляет тем, как объект, свойство или поле отображаются в окнах переменных отладчика.

**Когда?** Вам нужно [закрепить свойства](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips) в отладчике программным способом в коде.

**Зачем?** Закрепление свойств позволяет быстро проверять объекты по их свойствам, перенося указанное свойство в верхнюю часть списка свойств объекта в отладчике. 

## <a name="how-to"></a>Практические советы

1. Поместите курсор на тип, делегат, свойство или поле. 

2. Нажмите клавиши **CTRL**+ **.** чтобы активировать меню **Быстрые действия и рефакторинг** и выбрать **Добавить атрибут DebuggerDisplay**.

    ![Создание операторов сравнения](media/add-debugger-display-attribute.png)

3. Атрибут DebuggerDisplay будет добавлен вместе с методом auto, который возвращает значение ToString () по умолчанию. 

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
