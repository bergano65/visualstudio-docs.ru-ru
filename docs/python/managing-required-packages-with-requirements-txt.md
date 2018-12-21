---
title: Управление зависимостями пакета с помощью файла requirements.txt
description: Файл requirements.txt описывает зависимости проекта. Если вы получаете проект, содержащий файл requirements.txt, эти зависимости можно легко установить за один шаг.
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
ms.openlocfilehash: 1f6fefdeac06d28229b99a79f432f82ed844d950
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066182"
---
# <a name="manage-required-packages-with-requirementstxt"></a>Управление необходимыми пакетами с помощью requirements.txt

Если вы предоставляете доступ к проекту другим, используете систему сборки или планируете скопировать проект в другое расположение, где нужно восстановить среду, то необходимо указать внешние пакеты, необходимые проекту. Рекомендуется использовать файл [requirements.txt](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), содержащий список команд для pip, который устанавливает необходимые версии зависимых пакетов. Наиболее распространенной является команда `pip freeze > requirements.txt`, которая записывает текущий список пакетов среды в файл *requirements.txt*.

Технически для отслеживания требований можно использовать любой файл (используя `-r <full path to file>` при установке пакета), но Visual Studio имеет встроенную поддержку *requirements.txt*:

- Если вы загрузили проект, содержащий файл *requirements.txt*, и хотите установить все указанные в нем пакеты, разверните узел **Среды Python** в **обозревателе решений**, щелкните правой кнопкой мыши узел среды и выберите **Установить из файла requirements.txt**:

    ![Установка из файла requirements.txt](media/environments-requirements-txt-install.png)

- Если в среде установлены все необходимые пакеты, можно щелкнуть среду правой кнопкой мыши в **обозревателе решений** и выбрать **Создать файл requirements.txt**, чтобы создать необходимый файл. Если файл уже существует, отображается запрос с вариантами обновления:

    ![Параметры обновления файла requirements.txt](media/environments-requirements-txt-replace.png)

  - **Replace entire file** (Заменить весь файл) удаляет все существующие элементы, комментарии и параметры.
  - **Обновить существующие записи** определяет требования к пакету и обновляет описатели версии в соответствии с установленной версией.
  - **Update and add entries** (Обновить и добавить записи) обновляет имеющиеся требования и добавляет все другие пакеты в конец файла.

Так как файлы *requirements.txt* используются для фиксации требований среды, все установленные пакеты записываются с точными версиями. Такие версии позволяют легко воспроизвести ваше окружение на другом компьютере. Пакеты включены, даже если они были установлены с диапазоном версий, как зависимость от другого пакета или с установщиком, отличным от pip.

Если pip не удается установить пакет, указанный в файле *requirements.txt*, установка завершается сбоем. В этом случае нужно вручную исключить этот пакет из файла или использовать [параметры pip](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) для указания ссылки на устанавливаемую версию пакета. Например, можно использовать [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html) для компиляции зависимости и добавления параметра `--find-links <path>` в файл *requirements.txt*:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>См. также

- [Управление окружениями Python в Visual Studio](managing-python-environments-in-visual-studio.md)
- [Выбор интерпретатора для проекта](selecting-a-python-environment-for-a-project.md)
- [Пути поиска](search-paths.md)
- [Справочная информация по окну "Окружения Python"](python-environments-window-tab-reference.md)
