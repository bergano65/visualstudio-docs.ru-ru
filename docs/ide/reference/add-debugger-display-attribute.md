---
title: Добавление атрибута DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: db49bfd1672866a755cce6780527520da2cad420
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810393"
---
# <a name="add-debuggerdisplay-attribute"></a>Добавление атрибута DebuggerDisplay

Область применения этого формирования кода:

- C#

**Что?** [Атрибут DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) управляет тем, как объект, свойство или поле отображаются в окнах переменных отладчика.

**Когда?** Вам нужно [закрепить свойства](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) в отладчике программным способом в коде.

**Зачем?** Закрепление свойств позволяет быстро проверять объекты по их свойствам, перенося указанное свойство в верхнюю часть списка свойств объекта в отладчике. 

## <a name="how-to"></a>Практические советы

1. Поместите курсор на тип, делегат, свойство или поле. 

2. Нажмите клавиши **CTRL**+ **.** чтобы активировать меню **Быстрые действия и рефакторинг** и выбрать **Добавить атрибут DebuggerDisplay**.

    ![Создание операторов сравнения](media/add-debugger-display-attribute.png)

3. Атрибут DebuggerDisplay будет добавлен вместе с методом auto, который возвращает значение ToString () по умолчанию. 

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)