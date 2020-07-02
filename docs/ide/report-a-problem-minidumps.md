---
title: Создание минидампов со всеми стеками вызовов
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 8af2ef642a1c2422d470c716e14dca7d2e0168eb
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770840"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Создание минидампов со всеми стеками вызовов для процесса Visual Studio

В некоторых случаях специалисты Майкрософт могут запросить минидамп запущенного процесса Visual Studio со сведениями обо всех стеках вызовов. Чтобы собрать эти сведения, выполните описанные ниже действия.

## <a name="create-the-minidump-file"></a>Создание файла минидампа

1. Запустите новый экземпляр Visual Studio.
1. В главном меню выберите **Отладка** > **Присоединиться к процессу**.
1. Установите соответствующие флажки **Управляемый** и **Машинный код** и нажмите кнопку **Присоединиться**.

   ![Присоединение к процессу](../ide/media/attach-to-process.png)

1. В списке запущенных процессов выберите другой экземпляр Visual Studio для присоединения.
1. В главном меню выберите **Отладка** > **Прервать все**.
1. В главном меню выберите **Отладка** > **Сохранение дампа**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Получение стека вызовов из минидампа

1. Откройте файл дампа в Visual Studio.
1. Выберите **Средства** > **Параметры** > **Отладка** > **Символы** и установите флажок **Серверы символов (Майкрософт)** в разделе **Расположение файлов символов (PDB)** .
1. Откройте окно **Команда** (**Вид** > **Другие окна** > **Окно команд**).
1. Введите "~*k". В окне отобразятся все стеки вызовов потоков.
1. Скопируйте весь текст из окна "Команда" и сохраните в текстовый файл.
1. Вложите файл TXT в описание ошибки.
