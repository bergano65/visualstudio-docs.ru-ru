---
title: Установка средств искусственного интеллекта
description: Описание установки средств искусственного интеллекта для Visual Studio
keywords: искусственный интеллект, visual studio
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: cdbabcc9288a2f878b4c8cd86dbba97922f471c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841449"
---
# <a name="installation"></a>Установка

Инструменты Visual Studio для сценариев ИИ можно устанавливать в 64-разрядных операционных системах Windows.

## <a name="install-visual-studio-tools-for-ai"></a>Установка Visual Studio Tools for AI

Это расширение работает с Visual Studio 2015 и Visual Studio 2017 выпуска Community или более высокого уровня.

Скачать эти средства можно с сайта [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vstoolsai-vs2017) или из Visual Studio.

1. Выберите **Сервис** > **Расширения и обновления**.

   ![Меню "Расширения и обновления" в Visual Studio](media/installation/extensions.png)

2. В диалоговом окне **Расширения и обновления** выберите **Online** (Онлайн) с левой стороны.
3. В поле поиска в правом верхнем углу введите "tools for ai" (средства ИИ).
4. В результатах выберите **Visual Studio Tools for AI** (Средства Visual Studio для ИИ).
5. Выберите **Загрузить**.

## <a name="prepare-your-local-machine"></a>Подготовка локального компьютера
Перед обучением моделей глубокого обучения на локальном компьютере убедитесь в том, что установлены требуемые компоненты. В их число входят последние версии драйверов и библиотек для GPU NVIDIA (если применимо). Убедитесь также в том, что установлены среда и библиотеки Python, такие как NumPy и SciPy, и соответствующие платформы глубокого обучения, такие как Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch и Chainer, которые планируется использовать в проекте.

> [!NOTE]
> Краткие сведения о программном обеспечении в следующих подразделах взяты с домашних страниц соответствующих продуктов.

### <a name="nvidia-gpu-driver"></a>Драйвер GPU NVIDIA

Платформы глубинного обучения используют GPU NVIDIA, чтобы повысить скорость, точность и масштаб обучения искусственного интеллекта. Если на компьютере установлены видеоадаптеры NVIDIA, ознакомьтесь со страницей [скачивания драйверов NVIDIA](https://www.nvidia.com/Download/index.aspx) или попробуйте обновить операционную систему, чтобы установить последнюю версию драйвера.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) — это платформа параллельных вычислений и модель программирования, разработанная компанией NVIDIA. Она существенно увеличивает производительность вычислений благодаря использованию возможностей GPU. В настоящее время для платформ глубинного обучения требуется набор инструментов CUDA 8.0.

Установка CUDA

- Перейдите на этот [сайт](https://developer.nvidia.com/cuda-80-ga2-download-archive), скачайте и установите CUDA.
- Установите библиотеки CUDA времени выполнения, а затем добавьте путь к двоичным файлам CUDA в переменную среды %PATH% или $Path.
- В Windows путь по умолчанию — "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

![Установка CUDA в Windows](media/installation/install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network library, библиотека CUDA для глубинных нейронных сетей) — это GPU-ускоренная библиотека примитивов для глубинных нейронных сетей от NVIDIA. Для новейших платформ глубинного обучения требуется cuDNN v6.

Установка cuDNN:

- Перейдите на страницу [NVIDIA Developer](https://developer.nvidia.com/rdp/cudnn-download), чтобы скачать и установить последнюю версию пакета.
- Добавьте каталог, содержащий двоичный файл cuDNN, в переменную среды %PATH% или $Path.
- В Windows можно скопировать файл cudnn64_6.dll в каталог "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

> [!NOTE]
> Более ранние платформы глубинного обучения, такие как CNTK 2.0 и TensorFlow 1.2.1, требуют библиотеки cuDNN v5.1. Можно одновременно установить несколько версий cuDNN.

### <a name="python"></a>Python

Python является основным языком программирования для приложений глубинного обучения. Требуется **64-разрядный** дистрибутив Python. Для обеспечения максимальной совместимости рекомендуется версия [Python 3.5.4](https://www.python.org/downloads/release/python-354/).

### <a name="to-install-python-on-windows"></a>Установка Python в Windows

- Мы рекомендуем установить средство запуска Python только для себя и добавить Python в переменную среды %PATH%.
- Обязательно установите pip — систему управления пакетами, которая позволяет устанавливать программные пакеты, написанные на Python, и управлять ими.

Платформы глубинного обучения требуют pip для установки.

![Установка Python в Windows](media/installation/install_python_win.png)

Затем необходимо проверить, правильно ли установлен Python 3.5, и обновить систему pip до последней версии, выполнив в терминале следующие команды:

- **Windows**

  ```cmd
  C:\Users\test>python -V
  Python 3.5.4

  C:\Users\test>pip3.5 -V
  pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

  C:\Users\test>python -m pip install -U pip
  ```

- **macOS**

  ```bash
  MyMac:~ test$ python3.5 -V
  Python 3.5.4

  MyMac:~ test$ pip3.5 -V
  pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

  MyMac:~ test$ python3.5 -m pip install -U pip
  ```

### <a name="python-on-visual-studio"></a>Python в Visual Studio

Python полностью поддерживается в Visual Studio благодаря расширениям.
Получите дополнительные сведения об установке [Инструментов Python для Visual Studio](../python/installing-python-support-in-visual-studio.md).

### <a name="numpy-and-scipy"></a>NumPy и SciPy

- **NumPy** — это пакет обработки массивов общего назначения, который предназначен для эффективной работы с большими многомерными массивами произвольных элементов и в то же время позволяет работать с небольшими многомерными массивами без значительного снижения быстродействия.

- **SciPy** (произносится "сай пай") — это программное обеспечение с открытым кодом для математических, научных и инженерных вычислений, которое зависит от NumPy. Начиная с версии SciPy 1.0.0 предлагается официальный предварительно собранный пакет wheel для Windows.

Чтобы установить NumPy и SciPy, выполните в терминале следующую команду:

```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
> Приведенная выше команда обновляет существующие старые и неофициальные пакеты NumPy и SciPy (например, пакеты сторонних разработчиков для Windows со страницы http://www.lfd.uci.edu/~gohlke/pythonlibs/ ) до последних официальных версий пакетов.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) — это единый набор средств глубинного обучения, который описывает нейронные сети как ряд вычислительных шагов в виде направленного графа. CNTK поддерживает языки программирования Python и BrainScript.

> [!NOTE]
> В настоящее время CNTK не поддерживает macOS.

Сведения об установке пакета CNTK для Python см. в этой [статье](/cognitive-toolkit/Setup-CNTK-on-your-machine).

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) — это библиотека ПО с открытым кодом для числовых вычислений с использованием графов потоков данных. Подробные инструкции по установке см. [здесь](https://www.tensorflow.org/install/).

> [!NOTE]
> Начиная с версии 1.2 TensorFlow больше не предоставляет поддержку GPU в macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) — это простая, модульная, масштабируемая платформа глубинного обучения. Она построена на основе платформы Caffe и призвана обеспечить максимальное быстродействие и модульность.

В настоящее время готовый пакет wheel на Python для Caffe2 отсутствует.

Сведения о том, как выполнить сборку на основе исходного кода, см. [здесь](https://caffe2.ai/docs/getting-started.html).

### <a name="mxnet"></a>MXNet

[Apache MXNet (инкубатор)](https://mxnet.incubator.apache.org/) — это платформа глубинного обучения, призванная обеспечить максимальную эффективность и гибкость. Она позволяет **сочетать** [символическое и императивное программирование](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) для достижения максимальной эффективности и продуктивности.

Чтобы установить MXNet, выполните в терминале следующую команду:

- С GPU:

  ```bash
  pip3.5 install mxnet-cu80==0.12.0
  ```

- Без GPU:

  ```bash
  pip3.5 install mxnet==0.12.0
  ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) — это высокоуровневый API для нейронных сетей, написанный на Python, который может работать поверх CNTK, TensorFlow или Theano. Главной целью при его разработке являлось обеспечение быстрого проведения экспериментов. Минимальная задержка на пути от идеи к результату — ключевой фактор успешного исследования.

Чтобы установить Keras, выполните в терминале следующую команду:

```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) — это библиотека Python, которая позволяет эффективно определять, оптимизировать и вычислять математические выражения с многомерными массивами.

Чтобы установить Theano, выполните в терминале следующую команду:

```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](https://pytorch.org/) — это пакет Python, который представляет две высокоуровневые возможности:

- тензорные вычисления (как и в случае с NumPy) с эффективным ускорением на базе GPU;
- построение глубинных нейронных сетей на основе ленточной системы autograd.

Чтобы установить PyTorch, выполните в терминале следующую команду:

- **Windows**

  Официального пакета wheel пока нет. Можно загрузить сторонний пакет из [Anaconda](https://anaconda.org/pytorch/repo?type=all) или [Калифорнийского университета](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pytorch).

  - Распакуйте его в домашнем каталоге, например *C:\Users\test\pytorch*.
  - Добавьте каталог *C:\Users\test\pytorch\Lib\site-packages* в переменную среды %PYTHONPATH%.

    ```bash
    pip3 install http://download.pytorch.org/whl/cu80/torch-0.4.0-cp36-cp36m-win_amd64.whl
    pip3 install torchvision
    ```

- **macOS**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
  ```

  > [!NOTE]
  > Двоичные файлы macOS не поддерживают CUDA. Если требуется CUDA, выполните установку из источника.

- **Linux**

  ```bash
  pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
  ```

  > [!NOTE]
  > Этот пакет поддерживает как GPU, так и ЦП.

Наконец, установите torchvision в ОС, отличных от Windows:

```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) — это платформа глубинного обучения на основе Python, призванная обеспечить гибкость. Она предоставляет интерфейсы API автоматической дифференциации на основе подхода define-by-run (динамические вычислительные графы), а также высокоуровневые объектно-ориентированные интерфейсы API для построения и обучения нейронных сетей.

Чтобы включить поддержку CUDA, установите [CuPy](https://github.com/cupy/cupy):

```bash
pip3.5 install cupy
```

> [!NOTE]
> В Windows требуется версия 2015 среды [Visual Studio](https://visualstudio.microsoft.com/) или [Microsoft Visual C++ Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) для компиляции CuPy с использованием CUDA 8.0.

Чтобы установить Chainer, выполните в терминале следующую команду:

```bash
pip3.5 install chainer==3.0.0
```
