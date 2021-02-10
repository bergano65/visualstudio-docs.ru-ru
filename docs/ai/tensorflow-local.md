---
title: Локальное обучение модели tensorflow
description: Локальный запуск модели tensorflow в Инструментах Visual Studio для сценариев ИИ
keywords: ии, visual studio, tensorflow, локально
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: quickstart
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 0ceb21701958630c8b783d5b6850c5e0a0ab229a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841384"
---
# <a name="train-a-tensorflow-model-locally"></a>Локальное обучение модели tensorflow

В этом кратком руководстве мы обучим модель TensorFlow локально с помощью набора данных [MNIST](http://yann.lecun.com/exdb/mnist/) в Инструментах Visual Studio для сценариев ИИ.

База данных MNIST содержит обучающий набор из 60 000 примеров и тестовый набор из 10 000 примеров рукописных цифр.

## <a name="prerequisites"></a>предварительные требования

Прежде чем начать, убедитесь в том, что установлены следующие компоненты:

### <a name="google-tensorflow"></a>Google TensorFlow

В терминале выполните следующую команду:

```cmd
C:\>pip.exe install tensorflow
```

### <a name="numpy-and-scipy"></a>NumPy и SciPy
Установите [NumPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) и [SciPy](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy).

### <a name="download-sample-code"></a>Скачивание примера кода
Скачайте [репозиторий GitHub](https://github.com/Microsoft/samples-for-ai), содержащий образцы для начала работы с глубинным обучением на основе TensorFlow, CNTK, Theano и других библиотек.

## <a name="open-solution-and-train-model"></a>Открытие решения и обучение модели

- Запустите Visual Studio и выберите **Файл > Открыть > Решение или проект**.

- В скачанном репозитории с образцами выберите папку **Tensorflow Examples** и откройте файл **TensorflowExamples.sln**.

   ![Открытие проекта](media/tensorflow-local/open-project.png)

   ![Открытие решения](media/tensorflow-local/open-solution.png)

- В **обозревателе решений** найдите проект MNIST, щелкните его правой кнопкой мыши и выберите пункт **Назначить запускаемым проектом**.

- Нажмите **Запуск**.

- Выходные данные будут выведены в консоли.

   ![Пример выходных данных в консоли](media/tensorflow-local/console-output.png)

> [!div class="nextstepaction"]
> [Обучение модели TensorFlow в облаке](tensorflow-vm.md)
