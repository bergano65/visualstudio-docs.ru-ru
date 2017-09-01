---
title: "IPython REPL в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 9553aa4944f652c7b8505b0d99d5c2b88167f872
ms.contentlocale: ru-ru
ms.lasthandoff: 07/18/2017

---

# <a name="using-ipython-in-the-interactive-window"></a>Использование IPython в интерактивном окне

Интерактивное окно Visual Studio в режиме IPython предоставляет удобную интерактивную среду разработки с широкими возможностями, в том числе функцией интерактивных параллельных вычислений. Этот раздел описывает использование IPython в интерактивном окне Visual Studio, где также доступны все стандартные функции [интерактивного окна](interactive-repl.md).

Для работы вам потребуется установленное окружение [Anaconda](https://www.continuum.io), которое включает IPython и все необходимые библиотеки.

> [!Note]
> IronPython не поддерживает IPython, хотя его можно выбрать в форме параметров интерактивной работы. Дополнительные сведения см. в [запросе функции](https://github.com/Microsoft/PTVS/issues/84).

1. Откройте Visual Studio, переключитесь в окно окружения Python (**Просмотр > Другие окна > Окружения Python**) и выберите окружение Python, отобразившееся при запуске IPython.

1. Изучите данные на вкладке **Пакеты** (или **pip**) и убедитесь, что там указаны `IPython` и `matplotlib`. Если нет, установите их с помощью этой же вкладки.

1. Откройте вкладку **Обзор** и выберите **Использовать интерактивный режим IPython**. (В Visual Studio 2015 выберите **Configure interactive options** (Настройка интерактивных параметров), чтобы открыть диалоговое окно **Параметры**, укажите значение IPython для параметра **Interactive Mode** (Интерактивный режим) и нажмите кнопку **ОК**.)    

1. Выберите **Открыть интерактивное окно**, чтобы открыть интерактивное окно в режиме IPython. Если вы только что установили интерактивный режим, может потребоваться сброс установок окна, кроме того, может потребоваться нажать клавишу ВВОД, если отображается только приглашение ">>>".

    ![Интерактивное окно в режиме Python](media/ipython-repl-03.png)

1. Введите следующий код:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. После ввода последней строки прямо в этом же окне вы увидите график (размер которого при желании можно менять, перетаскивая его за нижний правый угол).

    ![Встроенный график в интерактивном окне](media/ipython-repl-04.png)

1. Вместо того чтобы вводить код прямо в окне REPL, вы можете написать его в редакторе, затем выбрать нужный фрагмент кода, щелкнуть правой кнопкой мыши и выбрать команду **Отправить в интерактивное окно** или нажать клавиши CTRL+ВВОД. Попробуйте вставить приведенный ниже код в новый файл в редакторе, а затем выбрать его, нажав клавиши CTRL+A, и отправить в интерактивное окно. (Обратите внимание, что Visual Studio отправляет код одним блоком, чтобы не создавать промежуточные или частичные графы. Кроме того, при отсутствии открытого проекта Python с выбранным другим окружением Visual Studio открывает интерактивное окно для любого окружения, выбранного в качестве используемого по умолчанию в окне **Окружения Python**.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![Отправка кода из редактора в интерактивное окно](media/ipython-repl-05.png)

1. Чтобы просмотреть график за пределами интерактивного окна, запустите код обычным образом, используя команду **Отладка > Запуск без отладки**.
    
IPython имеет множество других полезных функций, таких как экранирование символов для системной оболочки, подстановка переменных, запись вывода и т. д. Дополнительные сведения см. в [документации по IPython](http://ipython.org/documentation.html).

## <a name="related-topics"></a>См. также

- Чтобы легко пользоваться Jupyter без установки, попробуйте бесплатную [размещенную службу записных книжек Azure](https://notebooks.azure.com/), позволяющую сохранять и совместно использовать записные книжки.

- Кроме того, вы можете запустить Jupyter (прежнее название — IPython) на виртуальной машине под управлением Windows или Linux в Azure. Дополнительные сведения см. в разделе [Создание виртуальной машины Azure. Установка Jupyter и запуск записной книжки Jupyter в Azure](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).

