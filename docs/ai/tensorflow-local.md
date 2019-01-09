---
title: Локальное обучение модели tensorflow
description: Локальный запуск модели tensorflow в Инструментах Visual Studio для сценариев ИИ
keywords: ии, visual studio, tensorflow, локально
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: c6585eed1cfc6c4d9b57d6f6c66a8e4e2e93c5a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920382"
---
# <a name="train-a-tensorflow-model-locally"></a>Локальное обучение модели tensorflow

В этом кратком руководстве мы обучим модель TensorFlow локально с помощью набора данных [MNIST](http://yann.lecun.com/exdb/mnist/) в Инструментах Visual Studio для сценариев ИИ.

База данных MNIST содержит обучающий набор из 60 000 примеров и тестовый набор из 10 000 примеров рукописных цифр.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем начать, убедитесь в том, что установлены следующие компоненты:

### <a name="google-tensorflow"></a>Google TensorFlow

В терминале выполните следующую команду:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy и SciPy
Установите [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) и [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Скачивание образца кода
Скачайте [репозиторий GitHub](https://github.com/Microsoft/samples-for-ai), содержащий образцы для начала работы с глубинным обучением на основе TensorFlow, CNTK, Theano и других библиотек.

## <a name="open-solution-and-train-model"></a>Открытие решения и обучение модели

- Запустите Visual Studio и выберите **Файл > Открыть > Решение или проект**.

- В скачанном репозитории с образцами выберите папку **Tensorflow Examples** и откройте файл **TensorflowExamples.sln**.

   ![Открытие проекта](media/tensorflow-local/open-project.png)

   ![Открытие решения](media/tensorflow-local/open-solution.png)

- В **обозревателе решений** найдите проект MNIST, щелкните его правой кнопкой мыши и выберите пункт **Назначить запускаемым проектом**.

- Нажмите кнопку **Запустить**.

- Выходные данные будут выведены в консоли.

   ![Пример выходных данных в консоли](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Обучение модели TensorFlow в облаке](tensorflow-vm.md)