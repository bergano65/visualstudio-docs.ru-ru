---
title: "Работа с Python в Visual Studio, шаг 5 | Документы Майкрософт"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 82cb69b956a33fd23ad05833de9986980885483d
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2018
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Шаг 5. Установка пакетов в среде Python

**Предыдущий шаг: [выполнение кода в отладчике](vs-tutorial-01-04.md)**

Сообщество разработчиков на Python создало тысячи полезных пакетов, которые вы можете включать в свои проекты. В Visual Studio имеется пользовательский интерфейс для управления пакетами в средах Python.

1. Выберите в меню команды **Просмотр > Другие окна > Python Environments** (Среды Python). Откроется окно **Окружения Python**, в котором представлены различные среды, доступные вам. Список содержит как среды, установленные с помощью установщика Visual Studio, так и среды, которые вы установили отдельно. Среда, выделенная полужирным шрифтом, — это среда, используемая по умолчанию для новых проектов.

  ![Окно со средами Python](media/environments-default-view-blue.png)

1. На вкладке **Обзор** среды можно быстро получить доступ к интерактивному окну этой среды, а также к ее папке установки и интерпретаторам. Например, щелкните ссылку **Открыть интерактивное окно**, и в Visual Studio откроется интерактивное окно для этой среды.

1. Чтобы просмотреть список пакетов, установленных в настоящее время в среде, перейдите на вкладку **Пакеты**.

  ![Пакеты, установленные в среде](media/environments-installed-packages-blue.png)

1. Установите пакет `matplotlib`, введя его имя в поле поиска, а затем выбрав пункт `pip install`.

  ![Установка пакета matplotlib в среде](media/environments-add-matplotlib1.png)

1. Согласитесь на повышение прав, если появится соответствующий запрос.
 
1. После установки пакета он появится в окне "Окружения Python". Если щелкнуть знак **X** справа от пакета, он будет удален. 

  ![Завершение установки matplotlib в среде](media/environments-add-matplotlib2.png)

  Небольшой индикатор выполнения под названием среды указывает на то, что Visual Studio создает базу данных IntelliSense для нового пакета. На вкладке **IntelliSense** также приводятся более подробные сведения. Имейте в виду, что пока база данных не будет готова, функции IntelliSense, такие как автозавершение и проверка синтаксиса, будут неактивны для этого пакета в редакторе.

1. Создайте проект, выбрав пункт меню **Файл > Создать > Проект**, а затем выбрав шаблон "Приложение Python". В появившийся файл кода вставьте приведенный ниже код, который строит косинусоиду, как в предыдущих шагах учебника, но в теперь в виде графика.

    ```python
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt
    from math import radians

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Запустите программу с отладчиком (F5) или без него (CTRL+F5), чтобы увидеть результат.

  ![Выходные данные примера matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Работа с Git](vs-tutorial-01-06.md)

### <a name="going-deeper"></a>Дополнительные сведения

- [Среды Python](python-environments.md)
