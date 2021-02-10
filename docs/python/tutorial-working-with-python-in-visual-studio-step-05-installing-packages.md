---
title: Python в Visual Studio. Руководство. Шаг 5 — установка пакетов
titleSuffix: ''
description: Шаг 5 базового пошагового руководства, посвященного возможностям Python в Visual Studio. Здесь описаны функции Visual Studio для управления пакетами в окружении Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c47eacf0c9977e7342bfda17e03ea53728ee9215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901145"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Шаг 5. Установка пакетов в окружении Python

**Предыдущий шаг. [Выполнение кода в отладчике](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Сообщество разработчиков на Python создало тысячи полезных пакетов, которые вы можете включать в свои проекты. В Visual Studio имеется пользовательский интерфейс для управления пакетами в средах Python.

## <a name="view-environments"></a>Просмотр окружений

1. Выберите команду меню **Просмотр** > **Другие окна** > **Окружения Python**. Откроется окно **Окружения Python** (как узел **обозревателя решений**), в котором представлены разные среды, доступные вам. Список содержит как среды, установленные с помощью установщика Visual Studio, так и среды, которые вы установили отдельно. В их число входят глобальные, виртуальные среды и среды Conda. Среда, выделенная полужирным шрифтом, — это среда, используемая по умолчанию для новых проектов. Дополнительные сведения о работе со средами см. в разделе [Создание окружений Python и управление ими в средах Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Окно со средами Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Можно также открыть окно "Окружения Python", выбрав окно Обозревателя решений и нажав сочетание клавиш **CTRL+K, CTRL+`** . Если сочетание клавиш не работает и окно "Окружения Python" отсутствует в меню, возможно, не установлена рабочая нагрузка Python. Инструкции по установке Python см. в статье [Установка поддержки Python в Visual Studio](installing-python-support-in-visual-studio.md).

2. На вкладке **Обзор** среды можно быстро получить доступ к **интерактивному** окну этой среды, а также к ее папке установки и интерпретаторам. Например, щелкните ссылку **Открыть интерактивное окно**, и в Visual Studio откроется **интерактивное** окно для этой среды.

3. Теперь создайте проект, выбрав пункт меню **Файл** > **Создать** > **Проект**, а затем выбрав шаблон **Приложение Python**. В появившийся файл кода вставьте приведенный ниже код, который строит косинусоиду, как в предыдущих шагах учебника, но теперь в виде графика. Кроме того, можно использовать ранее созданный проект и заменить код.

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

4. В открытом проекте Python можно открыть окно "Окружения Python" из Обозревателя решений, щелкнув правой кнопкой мыши **Окружения Python** и выбрав **Просмотреть все окружения Python**.

   ![Среда](media/environments/environments-view-all-2019.png)

5. Если в окне редактора вы наведете указатель мыши на операторы импорта `numpy` и `matplotlib`, вы заметите, что они не разрешены. Это связано с тем, что пакеты не были установлены в глобальную среду по умолчанию.

   ![Неразрешенный импорт пакетов](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Установка пакетов с помощью окна "Окружения Python"

1. В окне "Окружения Python" выберите среду по умолчанию для новых проектов Python и перейдите на вкладку **Пакеты**. На ней вы увидите список пакетов, установленных в настоящее время в среде.

   ![Пакеты, установленные в среде](media/environments/environments-installed-packages-2019.png)

2. Установите пакет `matplotlib`, введя его имя в поле поиска, а затем выбрав параметр **Выполнить команду "pip install matplotlib"** . Будет установлен пакет `matplotlib`, а также все пакеты, от которых он зависит (в данном случае — `numpy`).

   ![Установка пакета matplotlib в среде](media/environments/environments-add-matplotlib-2019.png)

5. Согласитесь на повышение прав, если появится соответствующий запрос.

6. Установленный пакет появится в окне **Окружения Python**. Если щелкнуть знак **X** справа от пакета, он будет удален.

   ![Завершение установки matplotlib в среде](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Под названием среды может появиться небольшой индикатор выполнения, который указывает на то, что Visual Studio создает базу данных IntelliSense для нового пакета. На вкладке **IntelliSense** также приводятся более подробные сведения. Имейте в виду, что, пока база данных не будет готова, функции IntelliSense, такие как автозавершение и проверка синтаксиса, будут неактивны для этого пакета в редакторе.
   >
   > В Visual Studio 2017 версии 15.6 и более поздних версий используются другие (более быстрые) методы для работы с IntelliSense. На вкладке **IntelliSense** отображается соответствующее сообщение.

## <a name="run-the-program"></a>Запуск программы

1. После установки [matplotlib](https://matplotlib.org/) запустите программу с отладчиком (**F5**) или без него (**CTRL**+**F5**), чтобы увидеть результат.

   ![Выходные данные примера matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Работа с Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Дополнительные подробности

- [Среды Python](managing-python-environments-in-visual-studio.md)
- [Сведения о Django в Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Сведения о Flask в Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
