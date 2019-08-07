---
title: Создание минидампов со всеми стеками вызовов
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7d0580e04968a01dc8e447a9ee35f2b1c5934ccf
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461661"
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
