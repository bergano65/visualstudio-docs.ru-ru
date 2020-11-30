---
title: Добавление заголовка файла
description: Сведения о том, как использовать файл EditorConfig для добавления заголовков файлов в существующие файлы, проекты и решения.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f2e4715c0333b02f120ec5f92d9f742196c04f3
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870863"
---
# <a name="add-file-header"></a>Добавление заголовка файла

Область применения этого формирования кода:

- C#

- Visual Basic

**Что?** Добавление заголовков файлов в существующие файлы, проекты и решения с помощью [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

**Когда?** Если вам необходимо без лишних усилий добавить заголовки файлов к файлам, проектам и решениям.

**Зачем?** Если вам необходимо добавлять заголовки файлов для указания авторских прав. 

## <a name="how-to"></a>Практические советы

1. Добавьте [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) в проект или решение, если вы не сделали этого раньше.

2. Добавьте правило *file_header_template* в файл EditorConfig.

3. Задайте правилу значение, соответствующее тексту заголовка, который требуется добавить. В качестве заполнителя для имени файла можно использовать `{fileName}`.

    ![Снимок экрана: файл EditorConfig со значением file_header_template.](media/add-file-header-rule.png)

    > [!NOTE]
    > В EditorConfig нельзя явным образом указать несколько строк. Для добавления отдельных строк необходимо использовать символ новой строки, применяемый в системах Unix.

4. Поместите курсор на первую строку файла C# или Visual Basic.

5. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**.

6. Выберите **Add file header** (Добавить заголовок файла). 

    ![Снимок экрана: вариант с добавлением заголовка файла.](media/add-file-header.png)

7. Чтобы применить заголовок файла ко всем файлам проекта или решения, выберите **Project** (Проект) или **Solution** (Решение) для параметра **Fix all occurrences in** (Исправить все вхождения в).

8. Откроется диалоговое окно **Fix all occurrences** (Исправить все вхождения), где можно просмотреть вносимые изменения.

    ![Диалоговое окно Исправить все вхождения (Исправить все вхождения)](media/file-header-preview-changes.png)

8. Нажмите **Применить**, чтобы применить изменения.

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)