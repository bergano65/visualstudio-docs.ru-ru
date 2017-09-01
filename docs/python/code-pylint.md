---
title: "Использование PyLint в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 4b22d434b99bdd2648408b9191c5f050589883ae
ms.contentlocale: ru-ru
ms.lasthandoff: 08/14/2017

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

В разделе документации PyLint, посвященном [параметрам командной строки](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options), описывается управление поведением PyLint с помощью файла конфигурации `.pylintrc`. Этот файл можно разместить в корне проекта Python в Visual Studio или в другом месте, в зависимости от того, где нужно применять эти параметры.

Например, с помощью файла `.pylintrc` можно отключить предупреждение "отсутствует docstring", представленное на изображении выше. Для этого сделайте следующее:

1. В командной строке перейдите в корневой каталог проекта (где находится файл `.pyproj`) и выполните следующую команду, чтобы создать файл конфигурации с заметками:

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. В обозревателе решений Visual Studio щелкните проект правой кнопкой мыши, выберите **Добавить > Выход из элемента...**, затем найдите и выберите только что созданный файл `.pylintrc` и выберите команду **Добавить**.

1. Откройте файл для редактирования. Он содержит различные параметры, с которыми можно работать. Чтобы отключить это предупреждение, найдите раздел `[MESSAGES CONTROL]` и параметр `disable` в нем. Там находится длинная строка специальных сообщений, к которым можно добавить любые другие предупреждения. В нашем примере следует добавить `,missing-docstring` (включая запятую-разделитель).

1. Сохраните файл `.pylintrc`, снова запустите PyLint и убедитесь, что предупреждения больше не появляются.

