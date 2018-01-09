---
title: "Использование PyLint в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 032c6489463aaaee59b39423506f18bda82fb414
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-pylint-to-check-python-code"></a>Проверка кода Python с помощью PyLint

Широко распространенное средство [PyLint](https://www.pylint.org/) позволяет искать ошибки в коде Python и поощряет правильные методы создания кода Python. Это средство интегрируется в проекты Python для Visual Studio.

Просто щелкните правой кнопкой мыши проект Python в обозревателе решений и выберите **Python > Запуск PyLint...** :

![Команда PyLint в контекстном меню для проектов Python](media/code-pylint-command.png)

При запуске этой команды вы увидите предложение установить PyLint в вашем окружении, если это еще не сделано.

Предупреждения и ошибки PyLint отображаются в окне списка ошибок:

![Список ошибок PyLint](media/code-pylint-error-list.png)

Дважды щелкнув ошибку, вы перейдете к тому участку исходного кода, в котором она возникла.

> [!Tip]
> В разделе [документации по функциям PyLint](https://pylint.readthedocs.io/en/latest/technical_reference/features.html) вы можете найти полный список исходящих сообщений PyLint.

## <a name="setting-pylint-command-line-options"></a>Настройка параметров командной строки PyLint

В разделе документации PyLint, посвященном [параметрам командной строки](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options), описывается управление поведением PyLint с помощью файла конфигурации `.pylintrc`. Этот файл можно разместить в корне проекта Python в Visual Studio или в другом месте в зависимости от того, где нужно применять эти параметры (подробные сведения см. в описании [параметров командной строки](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)).

Например, с помощью файла `.pylintrc` можно отключить предупреждение "отсутствует docstring", представленное на изображении выше. Для этого сделайте следующее:

1. В командной строке перейдите в корневой каталог проекта (где находится файл `.pyproj`) и выполните следующую команду, чтобы создать файл конфигурации с заметками:

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. В обозревателе решений Visual Studio щелкните проект правой кнопкой мыши, выберите **Добавить > Выход из элемента...**, затем найдите и выберите только что созданный файл `.pylintrc` и выберите команду **Добавить**.

1. Откройте файл для редактирования. Он содержит различные параметры, с которыми можно работать. Чтобы отключить это предупреждение, найдите раздел `[MESSAGES CONTROL]` и параметр `disable` в нем. Там находится длинная строка специальных сообщений, к которым можно добавить любые другие предупреждения. В нашем примере следует добавить `,missing-docstring` (включая запятую-разделитель).

1. Сохраните файл `.pylintrc`, снова запустите PyLint и убедитесь, что предупреждения больше не появляются.

> [!Tip]
> Для использования файла `.pylintrc` из сетевой папки создайте переменную среды с именем `PYLINTRC` и присвойте ей в качестве значения имя файла в сетевой папке с указанием UNC-пути или буквы подключенного диска. Пример:
> ```
> PYLINTRC=\\myshare\python\.pylintrc
> ```
