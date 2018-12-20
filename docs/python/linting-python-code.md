---
title: Использование PyLint для кода Python
description: Запуск PyLint в Visual Studio для проверки проблем в коде Python, включая параметры командной строки для настройки анализа кода.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 52b9abf49176f37de98d47d87bc1d7ae265ded1e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066188"
---
# <a name="use-pylint-to-check-python-code"></a>Проверка кода Python с помощью PyLint

Широко распространенное средство [PyLint](https://www.pylint.org/) позволяет искать ошибки в коде Python и поощряет правильные методы создания кода Python. Это средство интегрируется в проекты Python для Visual Studio.

## <a name="run-pylint"></a>Выполнить PyLint

Щелкните правой кнопкой мыши проект Python в **обозревателе решений** и выберите **Python** > **Выполнить PyLint**:

![Команда PyLint в контекстном меню для проектов Python](media/code-pylint-command.png)

При запуске этой команды вы увидите предложение установить PyLint в вашем окружении, если это еще не сделано.

Предупреждения и ошибки PyLint отображаются в окне **Список ошибок**:

![Список ошибок PyLint](media/code-pylint-error-list.png)

Дважды щелкнув ошибку, вы перейдете к тому участку исходного кода, в котором она возникла.

> [!Tip]
> В разделе [документации по функциям PyLint](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) вы можете найти полный список исходящих сообщений PyLint.

## <a name="set-pylint-command-line-options"></a>Настройка параметров командной строки PyLint

В разделе документации PyLint, посвященном [параметрам командной строки](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options), описывается управление поведением PyLint с помощью файла конфигурации *.pylintrc*. Этот файл можно разместить в корне проекта Python в Visual Studio или в другом месте в зависимости от того, где нужно применять эти параметры (подробные сведения см. в описании [параметров командной строки](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)).

Например, с помощью файла *.pylintrc* можно отключить для проекта предупреждения "отсутствует docstring", представленное на изображении выше. Для этого сделайте следующее:

1. В командной строке перейдите в корневой каталог проекта (где находится файл *.pyproj*) и выполните следующую команду, чтобы создать файл конфигурации с заметками:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. В обозревателе решений Visual Studio щелкните проект правой кнопкой мыши, выберите **Добавить** > **Существующий элемент**, затем найдите и выберите только что созданный файл *.pylintrc* и выберите команду **Добавить**.

1. Откройте файл для редактирования. Он содержит различные параметры, с которыми можно работать. Чтобы отключить это предупреждение, найдите раздел `[MESSAGES CONTROL]` и параметр `disable` в нем. Там находится длинная строка специальных сообщений, к которым можно добавить любые другие предупреждения. В нашем примере следует добавить `,missing-docstring` (включая запятую-разделитель).

1. Сохраните файл *.pylintrc*, снова запустите PyLint и убедитесь, что предупреждения больше не появляются.

> [!Tip]
> Для использования файла *.pylintrc* из сетевой папки создайте переменную среды с именем `PYLINTRC` и присвойте ей в качестве значения имя файла в сетевой папке с указанием UNC-пути или буквы подключенного диска. Например, `PYLINTRC=\\myshare\python\.pylintrc`.
