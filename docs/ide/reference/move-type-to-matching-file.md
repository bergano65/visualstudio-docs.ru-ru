---
title: Рефакторинг для перемещения типа в соответствующий файл в Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 73e1d9d67d905fed5eb37e29c1be1ba7677da3e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884153"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Рефакторинг для перемещения типа в соответствующий файл

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Вы можете переместить выбранный тип в отдельный файл с таким же именем.

**Когда?** При наличии нескольких классов, структур, интерфейсов и пр. в одном файле, который нужно разделить.

**Зачем?** Размещение нескольких типов в одном файле может усложнить поиск этих типов. Перемещение типов в файлы с таким же именем улучшает читаемость кода и упрощает навигацию по нему.

## <a name="how-to"></a>Практические советы

1. Поместите курсор внутри имени типа, в котором он определен. Пример:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Затем выполните одно из следующих действий:

   - Нажмите клавиши **CTRL**+**.**
   - Щелкните правой кнопкой мыши имя типа и выберите **Quick Actions and Refactorings** (Быстрые действия и рефакторинг).

1. Выберите в меню **перемещение типа в *имя_типа*.cs**, где *имя_типа* — имя выбранного типа.

   Тип будет перемещен в новый файл в проекте с именем, совпадающим с именем типа.

   - C#:

      ![Встроенный результат — C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Встроенный результат — Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
