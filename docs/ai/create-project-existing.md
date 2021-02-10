---
title: Создание проекта ИИ на основе имеющегося кода
description: Сведения о том, как перенести существующий код Python в проект Visual Studio с помощью Visual Studio Tools for AI.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 7746d8dd39bb4400a7779ad43e489cf6e7475fb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841631"
---
# <a name="create-an-ai-project-from-existing-code"></a>Создание проекта ИИ на основе имеющегося кода

[Установив инструменты Visual Studio для сценариев ИИ](installation.md), вы можете легко перенести существующий код Python в проект Visual Studio.

> [!Important]
> Описанный здесь процесс не перемещает и не копирует исходные файлы. Если вы хотите работать с копией, сначала создайте дубликат папки.

1. Запустите Visual Studio и выберите **Файл > Создать > Проект**.

2. В диалоговом окне **Создание проекта** найдите **Инструменты ИИ**, выберите шаблон **На основе существующего кода Python**, укажите имя и расположение проекта, а затем нажмите кнопку **ОК**.

   ![Создание нового проекта из существующего кода, шаг 1](media/create-project-existing/new-ai-project.png)

3. В появившемся мастере задайте путь к существующему коду, выберите фильтр по типам файлов и укажите все нужные вашему проекту пути поиска, после чего нажмите кнопку **ОК**. Если вы не знаете пути поиска, оставьте это поле пустым.

   ![Создание нового проекта из существующего кода, шаг 2](media/create-project-existing/azurebatch-newproject.png)

   Если существующий код входит в проект решения "Машинное обучение Azure", установите флажок **Является папкой решения "Машинное обучение Azure"**, чтобы корректно преобразовать важные сведения о конфигурации решения "Машинное обучение Azure" (например, используемую учетную запись экспериментирования, рабочую область, контексты вычислений).

4. Чтобы указать файл запуска, найдите его в **обозревателе решений**, щелкните его правой кнопкой мыши и выберите пункт **Задать как файл запуска**.

5. Запустите программу, нажав клавиши **CTRL**+**F5** или выбрав пункты **Отладка > Запуск без отладки**.

> [!div class="nextstepaction"]
> [Учебник. Работа с Python в Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>См. также раздел

- [Определение существующего окружения Python вручную](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
