---
title: "IPython REPL в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>Использование Python в интерактивном окне

Интерактивное окно Visual Studio в режиме IPython предоставляет удобную интерактивную среду разработки с широкими возможностями, в том числе функцией интерактивных параллельных вычислений. В этой статье мы рассмотрим использование IPython в интерактивном окне Visual Studio. Для работы вам потребуется установленная среда [Anaconda](https://www.continuum.io), которая включает IPython и все необходимые библиотеки.

> [!Note]
> IronPython не поддерживает IPython, хотя его можно выбрать в форме параметров интерактивной работы. Если вам нужна такая возможность, поддержите [запрос на внедрение функции](https://github.com/Microsoft/PTVS/issues/84) или реализуйте ее самостоятельно.

1. Убедитесь, что пакет IPython установлен правильно. Для этого откройте каталог установки Python и запустите IPython в режиме Pylab:

  ```bash
  ipython --pylab
  ```

1. Введите следующий текст:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. Если все настроено правильно, вы увидите нечто подобное:

    ![Выходные данные конфигурации IPython ](~/docs/python/media/ipython-repl-01.png)

1. Откройте Visual Studio, переключитесь в окно среды Python (**Просмотр > Другие окна > Среды Python**) и выберите используемую среду Python.
1. Изучите данные на вкладке **pip** и убедитесь, что там указаны `IPython` и `matplotlib`. Если нет, установите их с помощью этой же вкладки.
1. Выберите вкладку **Обзор**, затем **Configure interactive options** (Настройка интерактивных параметров), укажите значение IPython для параметра **Interactive Mode** (Интерактивный режим) и нажмите **ОК**:

    ![Установка интерактивного режима IPython](~/docs/python/media/ipython-repl-02.png)

1. Выберите **Open interactive window** (Открыть интерактивное окно), чтобы открыть интерактивное окно в режиме IPython с PyLab. Если вы только что установили интерактивный режим, может потребоваться сброс установок окна:

    ![Интерактивное окно в режиме Python](~/docs/python/media/ipython-repl-03.png)

1. Введите следующий код:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. После ввода последней строки прямо в этом же окне вы увидите график (размер которого при желании можно менять, перетаскивая его за нижний правый угол).

    ![Встроенный график в интерактивном окне](~/docs/python/media/ipython-repl-04.png)

1. Вместо того чтобы вводить код прямо в окне PERL, вы можете написать его в редакторе, затем выбрать нужный фрагмент кода, щелкнуть правой кнопкой мыши и выбрать команду **Send to interactive** (Отправить в интерактивное окно) или нажать клавиши Ctrl+E, E. Попробуйте вставить приведенный ниже код в редактор, затем выбрать его, нажав клавиши Ctrl + A, и отправить код в интерактивное окно. (Обратите внимание, что при отправке кода в интерактивное окно Visual Studio передает его одним блоком, чтобы не создавать промежуточные или частичные графики).

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

    ![Отправка кода из редактора в интерактивное окно](~/docs/python/media/ipython-repl-05.png)

1. Чтобы просмотреть график за пределами интерактивного окна, запустите код обычным образом, используя команду **Отладка > Запуск без отладки**.
    
1. IPython имеет ряд полезных функций, таких как экранирование символов для системной оболочки, подстановка переменных, запись вывода и т. д. Дополнительные сведения вы найдете в руководстве по IPython.

    ![Экранирование символов для системной оболочки](~/docs/python/media/ipython-repl-06.png)

1. Также IPython можно использовать в режиме Notebook, открыв его в любом браузере на компьютере под управлением любой ОС. Ядро серверной части IPython может выполняться на локальном компьютере или удаленно. Azure поддерживает [выполнение IPython на виртуальной машине Windows или Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook). На странице [предварительной версии Azure Notebooks](https://notebooks.azure.com) вы можете бесплатно пользоваться Jupyter Notebooks в виде службы Azure.

    ![Режим Notebook для IPython](~/docs/python/media/ipython-repl-07.png)

