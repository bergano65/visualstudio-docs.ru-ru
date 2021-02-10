---
title: Запуск модели TensorFlow в облаке
description: запуск модели tensorflow в виртуальной машине azure для глубинного обучения
keywords: ии, visual studio, виртуальная машина для глубинного обучения
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: 8f6aef2d0cf8fe727036dda91256ac0330e15d37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841319"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Обучение модели TensorFlow в облаке

С помощью этого руководства мы обучим модель TensorFlow с помощью [набора данных MNIST](http://yann.lecun.com/exdb/mnist/) в виртуальной машине Azure для [глубинного обучения](/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview).

База данных MNIST содержит обучающий набор из 60 000 примеров и тестовый набор из 10 000 примеров рукописных цифр.

## <a name="prerequisites"></a>Предварительные требования
Прежде чем начать, убедитесь в том, что установлены и настроены следующие компоненты:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Настройка виртуальной машины Azure для глубинного обучения

> [!NOTE]
> В качестве **типа ОС** выберите Linux.

Инструкции по настройке виртуальной машины для глубинного обучения можно найти [здесь](/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Удаление комментария в скобках

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Скачивание образца кода

Скачайте [репозиторий GitHub](https://github.com/Microsoft/samples-for-ai), содержащий образцы для начала работы с глубинным обучением на основе TensorFlow, CNTK, Theano и других библиотек.

## <a name="open-project"></a>Открытие проекта

- Запустите Visual Studio и выберите **Файл > Открыть > Решение или проект**.

- В скачанном репозитории с образцами выберите папку **Tensorflow Examples** и откройте файл **TensorflowExamples.sln**.

   ![Открытие проекта](media/tensorflow-local/open-project.png)

   ![Открытие решения](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Добавление удаленной виртуальной машины Azure

В обозревателе сервера щелкните правой кнопкой мыши узел **Удаленные компьютеры** в узле "Средства ИИ" и выберите пункт "Добавить…". Введите отображаемое имя удаленного компьютера, IP-узел, порт SSH, имя пользователя и пароль или файл ключа.

![Добавление нового удаленного компьютера](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Отправка задания в виртуальную машину Azure
В **обозревателе решений** щелкните правой кнопкой мыши проект MNIST и выберите команду **Отправить задание**.

![Отправка задания на удаленный компьютер](media/tensorflow-vm/job-submission.png)

В окне отправки выполните указанные ниже действия.

- В списке **Используемый кластер** выберите удаленный компьютер (с префиксом "rm:"), куда нужно отправить задание.

- Введите **имя задания**.

- Нажмите кнопку **Отправить**.

## <a name="check-status-of-job"></a>Проверка состояния задания
Для просмотра состояния задания и сведений о нем разверните узел виртуальной машины, куда было отправлено задание, в **обозревателе сервера**. Дважды щелкните элемент **Задания**.

![Браузер заданий](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Очистка ресурсов

Остановите виртуальную машину, если планируете использовать ее в ближайшем будущем. Завершив работу с этим учебником, выполните следующую команду, чтобы очистить ресурсы:

```azurecli-interactive
az group delete --name myResourceGroup
```
