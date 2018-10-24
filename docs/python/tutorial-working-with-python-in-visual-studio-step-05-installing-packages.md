---
title: Руководство по работе с Python Шаг 5 — установка пакетов
description: Шаг 5 базового пошагового руководства, посвященного возможностям Python в Visual Studio. Здесь описаны функции Visual Studio для управления пакетами в окружении Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 02fdc0d7cd8a16ec7a00191a364def22ad2d8192
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939401"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Шаг 5. Установка пакетов в среде Python

**Предыдущий шаг: [выполнение кода в отладчике](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Сообщество разработчиков на Python создало тысячи полезных пакетов, которые вы можете включать в свои проекты. В Visual Studio имеется пользовательский интерфейс для управления пакетами в средах Python.

1. Выберите команду меню **Просмотр** > **Другие окна** > **Окружения Python**. Откроется окно **Окружения Python** (как узел **обозревателя решений**), в котором представлены разные среды, доступные вам. Список содержит как среды, установленные с помощью установщика Visual Studio, так и среды, которые вы установили отдельно. Среда, выделенная полужирным шрифтом, — это среда, используемая по умолчанию для новых проектов.

   ![Окно со средами Python](media/environments-default-view-blue.png)

2. На вкладке **Обзор** среды можно быстро получить доступ к **интерактивному** окну этой среды, а также к ее папке установки и интерпретаторам. Например, щелкните ссылку **Открыть интерактивное окно**, и в Visual Studio откроется **интерактивное** окно для этой среды.

3. Чтобы просмотреть список пакетов, установленных в настоящее время в среде, перейдите на вкладку **Пакеты**.

   ![Пакеты, установленные в среде](media/environments-installed-packages-blue.png)

4. Установите пакет `matplotlib`, введя его имя в поле поиска, а затем выбрав **pip install**.

   ![Установка пакета matplotlib в среде](media/environments-add-matplotlib1.png)

5. Согласитесь на повышение прав, если появится соответствующий запрос.

6. Установленный пакет появится в окне **Окружения Python**. Если щелкнуть знак **X** справа от пакета, он будет удален.

   ![Завершение установки matplotlib в среде](media/environments-add-matplotlib2.png)

   Под названием среды может появиться небольшой индикатор выполнения, который указывает на то, что Visual Studio создает базу данных IntelliSense для нового пакета. На вкладке **IntelliSense** также приводятся более подробные сведения. Имейте в виду, что пока база данных не будет готова, функции IntelliSense, такие как автозавершение и проверка синтаксиса, будут неактивны для этого пакета в редакторе.

   Обратите внимание, что в **Visual Studio 2017 версии 15.6** и более поздних версий используются другие (более быстрые) методы для работы с IntelliSense. На вкладке **IntelliSense** отображается соответствующее сообщение.

7. Создайте проект, выбрав пункт меню **Файл** > **Создать** > **Проект**, а затем выбрав шаблон **Приложение Python**. В появившийся файл кода вставьте приведенный ниже код, который строит косинусоиду, как в предыдущих шагах учебника, но в теперь в виде графика.

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

8. Запустите программу с отладчиком (**F5**) или без него (**CTRL**+**F5**), чтобы увидеть результат.

   ![Выходные данные примера matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Работа с Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Дополнительные подробности

- [Среды Python](managing-python-environments-in-visual-studio.md)
