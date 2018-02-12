---
title: "Краткое руководство. Создание проекта Python с помощью Cookiecutter в Visual Studio | Документация Майкрософт"
description: "Быстрое начало работы с помощью шаблона Cookiecutter в Python в Visual Studio."
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: quickstart
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: d5bb046ea51cd7068aa8b7acef0c886b858d0bc0
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Краткое руководство. Создание проекта на основе шаблона Cookiecutter

После [установки поддержки Python в Visual Studio 2017](installing-python-support-in-visual-studio.md) можно легко создать проект на основе шаблона Cookiecutter, включая множество шаблонов, опубликованных в GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) предоставляет графический пользовательский интерфейс для поиска шаблонов, ввода их параметров и создания проектов и файлов. В Visual Studio 2017 этот компонент уже встроен. В ранних версиях Visual Studio этот компонент нужно устанавливать отдельно.

1. Для этого краткого руководства сначала установите дистрибутив Python Anaconda3, который включает в себя необходимые пакеты Python для приведенного здесь шаблона Cookiecutter. Запустите установщик Visual Studio, выберите **Изменить**, разверните параметры **разработки Python** в правой части экрана и выберите Anaconda3 (32- или 64-разрядную версию). Имейте в виду, что установка может занять некоторое время в зависимости от скорости Интернета, но это самый простой способ установить необходимые пакеты.

1. Запустите Visual Studio.

1. Выберите **Файл > Создать > Из Cookiecutter...**. При выборе этой команды в Visual Studio открывается окно с шаблонами. 

    ![Создание проекта на основе шаблона Cookiecutter](media/projects-from-cookiecutter1.png)

1. Выберите шаблон "Microsoft/python-sklearn-classifier-cookiecutter" и нажмите кнопку **Далее**. (При первом использовании Cookiecutter процесс может занять несколько минут.)

1. В следующим шаге укажите расположение для нового проекта в поле **Создать в** и нажмите кнопку **Создать**.

    ![Второй этап работы с Cookiecutter, настройка свойств проекта](media/projects-from-cookiecutter2.png)

1. По завершении процесса появится сообщение "Файлы успешно созданы". Выберите команду **Открыть в обозревателе решений**, чтобы открыть проект.

1. Чтобы запустить программу, нажмите клавиши CTRL+F5 или последовательно выберите **"Отладка" > "Запустить без отладки"**. 

    ![Выходные данные проекта шаблона python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Руководство. Работа с Python в Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>См. также

- [Использование расширения Cookiecutter](using-python-cookiecutter-templates.md)
- [Создание среды для существующего интерпретатора Python](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Установка поддержки Python в Visual Studio 2015 и более ранних версиях](installing-python-support-in-visual-studio.md).
- [Расположения установки](installing-python-support-in-visual-studio.md#install-locations).
