---
title: "Использование PyLint в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
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
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: c8bfaf9f20e7fecb3633ca101170b0f3e686aa53
ms.lasthandoff: 04/10/2017

---

# <a name="using-pylint-to-check-python-code"></a>Проверка кода Python с помощью PyLint

Широко распространенное средство [PyLint](https://www.pylint.org/) позволяет искать ошибки в коде Python и поощряет правильные методы создания кода Python. Это средство интегрируется в проекты Python для Visual Studio.

Просто щелкните правой кнопкой мыши проект Python в обозревателе решений и выберите **Python > Запуск PyLint...**:

![Команда PyLint в контекстном меню для проектов Python](media/code-pylint-command.png)

При запуске этой команды вы увидите предложение установить PyLint в вашей среде, если это требуется.

Предупреждения и ошибки PyLint отображаются в окне списка ошибок:

![Список ошибок PyLint](media/code-pylint-error-list.png)

Дважды щелкнув ошибку, вы перейдете к тому участку исходного кода, в котором она возникла.

> [!Tip]
> В разделе [документации по функциям PyLint](https://pylint.readthedocs.io/en/latest/reference_guide/features.html) вы можете найти полный список исходящих сообщений PyLint.

## <a name="setting-pylint-command-line-options"></a>Настройка параметров командной строки PyLint

В разделе документации PyLint, посвященном [параметрам командной строки](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options), описывается управление поведением PyLint с помощью файла конфигурации `.pylintrc`. Этот файл можно разместить в корне проекта Python в Visual Studio или в другом месте, в зависимости от того, где нужно применять эти параметры.

Например, с помощью файла `.pylintrc` можно отключить предупреждение "отсутствует docstring", представленное на изображении выше. Для этого выполните следующее.

1. В командной строке перейдите в корневой каталог проекта (в котором находится файл `.pyproj`) и выполните следующую команду, чтобы создать файл конфигурации с комментариями:

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. В обозревателе решений Visual Studio щелкните проект правой кнопкой мыши, выберите **Добавить > Выход из элемента...**, затем найдите и выберите только что созданный файл `.pylintrc` и выберите команду **Добавить**.

1. Откройте файл для редактирования. В нем вы увидите различные параметры, с которыми можно работать. Чтобы отключить это предупреждение, найдите раздел `[MESSAGES CONTROL]`, а затем параметр `disable` ниже этого раздела. Вы увидите длинную строку специальных сообщений, к которым можно добавить любое другое предупреждение. В нашем примере следует добавить `,missing-docstring` (включая запятую-разделитель).

1. Сохраните файл `.pylintrc`, запустите PyLint и убедитесь, что предупреждение больше не появляется.
