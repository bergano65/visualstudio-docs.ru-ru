---
title: Краткое руководство. Создание проектов Python с помощью Cookiecutter
description: При помощи этого краткого руководства вы создадите проект Visual Studio для Python с помощью шаблона Cookiecutter.
ms.date: 02/25/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 4c8a3727faa01b69962dd3dc456ac7b704f62882
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902437"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Краткое руководство. Создание проекта из шаблона Cookiecutter

После [установки поддержки Python в Visual Studio](installing-python-support-in-visual-studio.md) можно легко создать проект на основе шаблона Cookiecutter, включая множество шаблонов, опубликованных в GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) предоставляет графический пользовательский интерфейс для поиска шаблонов, ввода их параметров и создания проектов и файлов. В Visual Studio 2017 и более поздних версий этот компонент уже встроен. В более ранних версиях Visual Studio его нужно устанавливать отдельно.

1. Для этого краткого руководства сначала установите дистрибутив Python Anaconda3, который включает в себя необходимые пакеты Python для приведенного здесь шаблона Cookiecutter. Запустите установщик Visual Studio, выберите **Изменить**, разверните параметры **разработки Python** в правой части экрана и выберите **Anaconda3** (32- или 64-разрядную версию). Имейте в виду, что установка может занять некоторое время в зависимости от скорости Интернета, но это самый простой способ установить необходимые пакеты.

1. Запустите Visual Studio.

1. Выберите **Файл** > **Создать** > **Из Cookiecutter**. При выборе этой команды в Visual Studio открывается окно с шаблонами.

    ![Создание проекта на основе шаблона Cookiecutter](media/projects-from-cookiecutter1.png)

1. Выберите шаблон **Microsoft/python-sklearn-classifier-cookiecutter** и щелкните **Далее**. (Этот процесс может занять несколько минут при первом использовании конкретного шаблона, так как Visual Studio устанавливает необходимые пакеты Python.)

1. В следующим шаге укажите расположение для нового проекта в поле **Создать в** и нажмите **Создать и открыть проект**.

    ![Второй этап работы с Cookiecutter, настройка свойств проекта](media/projects-from-cookiecutter2.png)

1. По завершении процесса появится сообщение **Файлы успешно созданы с помощью шаблона...** . Проект автоматически открывается в обозревателе решений.

1. Чтобы запустить программу, нажмите клавиши **CTRL**+**F5** или последовательно выберите **Отладка** > **Запустить без отладки**.

    ![Выходные данные проекта шаблона python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Учебник. Работа с Python в Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>См. также

- [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md)
- [Определение существующего интерпретатора Python вручную](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Установка поддержки Python в Visual Studio 2015 и более ранних версиях](installing-python-support-in-visual-studio.md)
- [Расположения установки](installing-python-support-in-visual-studio.md#install-locations)
