---
title: Добавление заголовка файла
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 779092e277ac5b6eed3afcaceaf55b26ee2759dd
ms.sourcegitcommit: 025816f8e388b29e58761d304b0fda755ac5a613
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374173"
---
# <a name="add-file-header"></a>Добавление заголовка файла

Область применения этого формирования кода:

- C#

- Visual Basic

**Что?** Добавление заголовков файлов в существующие файлы, проекты и решения с помощью [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

**Когда?** Если вам необходимо без лишних усилий добавить заголовки файлов к файлам, проектам и решениям.

**Зачем?** Если вам необходимо добавлять заголовки файлов для указания авторских прав. 

## <a name="how-to"></a>Практические советы

1. Добавьте [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) в проект или решение, если вы не сделали этого раньше.

2. Добавьте правило *file_header_template* в файл EditorConfig.

3. Задайте правилу значение, соответствующее тексту заголовка, который требуется добавить.

    ![Правило заголовка файла EditorConfig](media/add-file-header-rule.png)

> [!NOTE]
> В EditorConfig нельзя явным образом указать несколько строк. Для добавления отдельных строк необходимо использовать символ новой строки, применяемый в системах Unix.

4. Поместите курсор на первую строку файла C# или Visual Basic.

5. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

6. Выберите **Add file header** (Добавить заголовок файла). 

    ![Правило заголовка файла EditorConfig](media/add-file-header.png)

7. Чтобы применить заголовок файла ко всем файлам проекта или решения, выберите **Project** (Проект) или **Solution** (Решение) для параметра **Fix all occurrences in** (Исправить все вхождения в).

8. Откроется диалоговое окно **Fix all occurrences** (Исправить все вхождения), где можно просмотреть вносимые изменения.

    ![Диалоговое окно Исправить все вхождения (Исправить все вхождения)](media/file-header-preview-changes.png)

8. Нажмите **Применить**, чтобы применить изменения.

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
