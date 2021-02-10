---
title: Определение пользовательских команд меню для проектов Python
description: Редактируя проекты и целевые файлы, вы можете добавлять настраиваемые команды в контекстное меню проекта Python в Visual Studio, чтобы вызывать исполняемые программы, скрипты, модули, встроенные фрагменты кода и команды pip.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 43270ee1ec956f45b76d23a6b649ad2d870638c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887930"
---
# <a name="define-custom-commands-for-python-projects"></a>Определение пользовательских команд для проектов Python

В процессе работы с проектами Python вам может потребоваться переключиться в командное окно для выполнения определенных скриптов или модулей, команд pip или запуска другого произвольного средства. Чтобы улучшить рабочий процесс, можно добавить пользовательские команды в подменю **Python** внутри контекстного меню проекта Python. Эти команды можно выполнять в окне консоли или в окне **вывода** Visual Studio. Кроме того, вы можете использовать регулярные выражения, чтобы сообщить Visual Studio, как анализировать ошибки и предупреждения из выходных данных команды.

По умолчанию это меню содержит только одну команду **Выполнить PyLint**:

![Внешний вид по умолчанию для подменю Python внутри контекстного меню проекта](media/custom-commands-default-menu.png)

В этом же контекстном меню отображаются пользовательские команды. Пользовательские команды добавляются напрямую в файл проекта, после чего применяются к конкретному проекту. Вы также можете определить пользовательские команды в файле *TARGETS*, который легко импортировать в несколько файлов проектов.

Некоторые шаблоны проектов Python в Visual Studio уже добавляют собственные команды посредством своего файла *TARGETS*. Например, шаблоны "Веб-проект Bottle" и "Веб-проект Flask" добавляют две команды — **Запуск сервера** и **Запустить сервер отладки**. Шаблон "Веб-проект Django" добавляет как эти две команды, так и многие другие:

![Внешний вид подменю Python внутри контекстного меню проекта Django](media/custom-commands-django-menu.png)

Каждая пользовательская команда может ссылаться на файл Python, модуль Python, встроенный код Python, произвольный исполняемый файл или команду pip. Вы можете указать, как и где выполняется команда.

> [!Tip]
> При внесении изменений в файл проекта в текстовом редакторе нужно перезагрузить проект в Visual Studio, чтобы применить эти изменения. Например, нужно перезагрузить проект после добавления определений пользовательских команд, чтобы эти команды отображались в контекстном меню проекта.
>
> Как вы знаете, Visual Studio предоставляет средства для редактирования файлов проекта напрямую. Щелкните правой кнопкой мыши файл проекта и выберите команду **Выгрузить проект**, а затем снова щелкните правой кнопкой и выберите **Изменить \<project-name>** , чтобы открыть проект в редакторе Visual Studio. После этого внесите и сохраните изменения, еще раз щелкните проект правой кнопкой мыши и выберите **Перезагрузить проект**, после чего вам будет предложено подтвердить закрытие файла проекта в редакторе.
>
> Однако при разработке пользовательской команды эти действия могут утомлять пользователя. Чтобы повысить эффективность работы, загрузите проект в Visual Studio и параллельно откройте файл *PYPROJ* в отдельном редакторе (например, в другом экземпляре Visual Studio, Visual Studio Code, Блокноте и т. д.). Когда вы сохраняете изменения в редакторе и переключаетесь в Visual Studio, Visual Studio обнаруживает изменения и предлагает перезагрузить проект (**Проект \<name> был изменен вне среды.** ). Выберите **Перезагрузить**, чтобы сразу же применить внесенные изменения за одно действие.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Пошаговое руководство. Добавление команды в файл проекта

Для ознакомления с пользовательскими командами в этом разделе рассматривается простой пример, в котором файл запуска проекта выполняется напрямую с помощью *python.exe*. (Такая команда фактически аналогична использованию команды **Отладка** > **Запуск без отладки**.)

1. Создайте проект с именем Python-CustomCommands, используя шаблон **Приложение Python**. (Если вы еще не знакомы с этой процедурой, см. инструкции в статье [Краткое руководство. Создание проекта Python из шаблона](quickstart-02-python-in-visual-studio-project-from-template.md).)

1. В *Python_CustomCommands.py* добавьте код `print("Hello custom commands")`.

1. Щелкните проект правой кнопкой мыши в **обозревателе решений**, выберите **Python** и обратите внимание, что в подменю отображается только команда **Выполнить PyLint**. В этом же подменю отображаются и ваши пользовательские команды.

1. Откройте *Python-CustomCommands.pyproj* в отдельном текстовом редакторе, как описано во введении. Добавьте следующие строки в конец файла внутри прямо перед закрывающим `</Project>` и сохраните файл.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Вернитесь в Visual Studio и выберите **Перезагрузить** при выводе запроса об изменении файла. Затем проверьте меню **Python** еще раз и убедитесь, что единственным элементом там по-прежнему является команда **Выполнить PyLint**, так как добавленные строки просто реплицируют группу свойств по умолчанию `<PythonCommands>`, содержащую команду PyLint.

1. Переключитесь в редактор с файлом проекта и добавьте следующее определение `<Target>` после `<PropertyGroup>`. Как описано далее в этой статье, этот элемент `Target` определяет пользовательскую команду для выполнения файла запуска (определяется свойством StartupFile) с помощью *python.exe* в окне консоли. Атрибут `ExecuteIn="consolepause"` использует консоль, которая ожидает нажатия клавиши перед закрытием.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Добавьте значение атрибута `Name` Target в добавленную ранее группу свойств `<PythonCommands>`, чтобы элемент выглядел аналогично приведенному ниже коду. Добавление имени целевого объекта в этот список — это фактически и добавление его в меню **Python**.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Чтобы команда отображалась перед командами, заданными в `$(PythonCommands)`, расположите их перед этим токеном.

1. Сохраните файл проекта, перейдите в Visual Studio и перезагрузите проект при появлении запроса. Затем щелкните проект **Python-CustomCommands** правой кнопкой мыши и выберите пункт **Python**. В меню вы увидите элемент **Run startup file** (Выполнить файл запуска). Если такой элемент в меню отсутствует, убедитесь, что вы добавили это имя в элемент `<PythonCommands>`. См. также раздел [Устранение неполадок](#troubleshooting) далее в этой статье.

    ![Пользовательские команды, отображаемые в контекстном подменю Python](media/custom-commands-walkthrough-menu-item.png)

1. Выберите команду **Выполнить файл запуска**, чтобы отобразить командное окно с текстом **Hello custom commands** (Знакомство с пользовательскими командами) и запросом **Press any key to continue** (Для продолжения нажмите любую клавишу).  Нажмите любую клавишу, чтобы закрыть окно.

    ![Выходные данные пользовательской команды в окне консоли](media/custom-commands-walkthrough-console.png)

1. Вернитесь в редактор с файлом проекта и измените значение атрибута `ExecuteIn` на `output`. Сохраните файл, перейдите в Visual Studio, перезагрузите проект и вызовите эту команду снова. На этот раз выходные данные программы отображаются в окне **Вывод** Visual Studio:

    ![Выходные данные пользовательской команду в окне вывода](media/custom-commands-walkthrough-output-window.png)

1. Чтобы добавить дополнительные команды, определите для каждой из них подходящий элемент `<Target>`, добавьте имя целевого объекта в группу свойств `<PythonCommands>` и перезагрузите проект в Visual Studio.

>[!Tip]
> Если вызвать команду, использующую свойства проекта, например `($StartupFile)`, которая завершается с ошибкой из-за неопределенного токена, Visual Studio отключает эту команду до перезагрузки проекта. Однако внесение в проект изменений, определяющих это свойство, не обновляет состояние этих команд, поэтому в подобных ситуациях все равно нужно перезагрузить проект.

## <a name="command-target-structure"></a>Структура целевого объекта команды

Общая форма элемента `<Target>` показана в следующем псевдокоде:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Чтобы сослаться на свойства проекта или переменные среды в значениях атрибутов, используйте имя в токене `$()`, например `$(StartupFile)` и `$(MSBuildProjectDirectory)`. Дополнительные сведения см. в разделе [Свойства MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Атрибуты Target

| Атрибут | Обязательное значение | Описание |
| --- | --- | --- |
| name | Да | Идентификатор для команды в проекте Visual Studio. Это имя нужно добавить в группу свойств `<PythonCommands>`, чтобы команда появилась в подменю Python. |
| Метка | Да | Отображаемое имя пользовательского интерфейса, отображаемое в подменю Python. |
| Возвращает | Да | Должен содержать `@(Commands)`, который идентифицирует целевой объект как команду. |

### <a name="createpythoncommanditem-attributes"></a>Атрибуты CreatePythonCommandItem

Все значения атрибутов указываются без учета регистра.

| Атрибут | Обязательное значение | Описание |
| --- | --- | --- |
| TargetType | Да | Указывает, что содержит атрибут Target и как он используется вместе с атрибутом Arguments:<ul><li>**executable**. Запуск исполняемого файла с именем, указанным в Target, с добавлением значения в Arguments, как при вводе непосредственно в командной строке. Это значение должно содержать только имя программы без аргументов.</li><li>**script**. Запуск *python.exe* с именем файла в Target, после которого идет значение в Arguments.</li><li>**module**. Запуск `python -m`, после которого идет имя модуля в Target и значение в Arguments.</li><li>**code**. Запуск встроенного кода, содержащегося в Target. Значение Arguments игнорируется.</li><li>**pip**. Запуск `pip` с командой в Target, после которого идет Arguments; для ExecuteIn задано значение output, однако pip предполагает команду `install` и использует Target в качестве имени пакета.</li></ul> |
| целевого объекта | Да | Имя файла, имя модуля, код или команда pip, которые требуется использовать, в зависимости от TargetType. |
| Аргументы | Необязательный | Указывает строку аргументов (при их наличии) для передачи целевому объекту. Обратите внимание, что, когда TargetType имеет значение `script`, аргументы передаются программе Python, а не *python.exe*. Для TargetType `code` игнорируется. |
| ExecuteIn | Да | Определяет среду, в которой выполняется команда:<ul><li>**console**. Запускает Target и аргументы, как при вводе непосредственно в командной строке (по умолчанию). Командное окно отображается при выполнении Target, а затем автоматически закрывается.</li><li>**consolepause**. То же, что и console, но с ожиданием нажатия клавиши перед закрытием окна.</li><li>**output**. Запускает Target и отображает результаты в окне **вывода** Visual Studio. Если TargetType имеет значение pip, Visual Studio использует Target в качестве имени пакета и добавляет Arguments.</li><li>**repl**. Запускает Target в [интерактивном окне Python](python-interactive-repl-in-visual-studio.md); для заголовка окна используется необязательное отображаемое имя.</li><li>**none**: аналогичен console.</li></ul>|
| WorkingDirectory | Необязательный | Папка, в которой выполняется команда. |
| ErrorRegex<br>WarningRegEx | Необязательный | Используется, только если ExecuteIn имеет значение `output`. Оба значения указывают регулярное выражение, с помощью которого Visual Studio анализирует выходные данные команды, чтобы отобразить ошибки и предупреждения в окне **Список ошибок**. Если значение не указано, команда не затрагивает окно **Список ошибок**. Дополнительные сведения о том, что ожидает Visual Studio, см. в разделе [Именованные группы записи](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Необязательный | Список требований к пакету для команды, использующий тот же формат, что и [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (pip.readthedocs.io). Например, команда **Выполнить PyLint** указывает `pylint>=1.0.0`. Перед выполнением команды Visual Studio проверяет, что установлены все пакеты в списке. Для установки всех отсутствующих пакетов Visual Studio использует pip. |
| Среда | Необязательный | Строка с переменными среды, которые нужно определить перед выполнением команды. Каждая переменная использует формат \<NAME>=\<VALUE>, а для разделения нескольких переменных используется точка с запятой. Переменная с несколькими значениями должна быть заключена в одинарные или двойные кавычки, например 'имя=значение1;значение2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Именованные группы записи для регулярных выражений

При анализе ошибки и предупреждений из выходных данных команды Visual Studio ожидает, что регулярные выражения в значениях `ErrorRegex` и `WarningRegex` используют следующие именованные группы:

- `(?<message>...)`. Текст ошибки.
- `(?<code>...)`. Код ошибки
- `(?<filename>...)`. Имя файла, для которого возникла ошибка.
- `(?<line>...)`. Номер строки в файле, где произошла ошибка.
- `(?<column>...)`. Номер столбца в файле, где произошла ошибка.

Например, PyLint выводит предупреждения в следующем виде:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Чтобы разрешить Visual Studio извлечь правильную информацию из таких предупреждений и отобразить их в окне **Список ошибок**, значение `WarningRegex` для команды **Выполнить PyLint** имеет следующий вид:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Обратите внимание, что `msg_id` в значении должно быть `code`, см. описание [запроса 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Создание TARGETS-файлов с пользовательскими командами

Пользовательские команды, определенные в файле проекта, доступны только этому файлу. Чтобы использовать команды в нескольких файлах проектов, следует определить группу свойств `<PythonCommands>` и все ваши элементы `<Target>` в файле *TARGETS*. Затем этот файл можно импортировать в отдельные файлы проектов.

Файл *TARGETS* имеет следующий формат:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Чтобы загрузить файл *TARGETS* в проект, расположите элемент `<Import Project="(path)">` в любом месте внутри элемента `<Project>`. Например, если у вас есть файл с именем *CustomCommands.targets* во вложенной папке *targets* в проекте, используйте следующий код:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> При каждом изменении файла *TARGETS* нужно перезагружать *решение*, содержащее этот проект, а не только сам проект.

## <a name="example-commands"></a>Примеры команд

### <a name="run-pylint-module-target"></a>Выполнение PyLint (целевой объект модуля)

В файле *Microsoft.PythonTools.targets* отображается следующий код:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Запуск pip install с определенным пакетом (целевой объект pip)

Следующая команда запускает `pip install my-package` в окне **вывода**. Эту команду можно использовать при разработке пакета и тестировании его установки. Обратите внимание, что Target содержит имя пакета, а не команду `install`, которая предполагается при использовании `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Отображение устаревших пакетов pip (целевой объект pip)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Запуск исполняемого файла с consolepause

Следующая команда просто запускает `where` для отображения файлов Python, начиная с папки проекта:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Выполнение команд запуска сервера и сервера отладки

Чтобы узнать, как определены команды **Запуск сервера** и **Запустить сервер отладки** для веб-проектов, см. [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Установка пакета для разработки

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Из файла [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), используемого с разрешениями.*

### <a name="generate-windows-installer"></a>Создание установщика Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Из файла [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), используемого с разрешениями.*

### <a name="generate-wheel-package"></a>Создание пакета wheel

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Из файла [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), используемого с разрешениями.*

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="message-the-project-file-could-not-be-loaded"></a>Сообщение: "Не удалось загрузить файл проекта"

Указывает на наличие синтаксических ошибок в файле проекта. Это сообщение содержит конкретную ошибку с номером строки и позицией символа.

### <a name="console-window-closes-immediately-after-command-is-run"></a>Окно консоли закрывается сразу после выполнения команды

Используйте `ExecuteIn="consolepause"` вместо `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Команда не отображается в меню

Убедитесь, что команда включена в группу свойств `<PythonCommands>`, а имя в списке команд совпадает с именем, указанным в элементе `<Target>`.

Например, в следующих элементах имя Example в группе свойств не соответствует имени ExampleCommand в целевом объекте. Visual Studio не находит команду с именем Example, поэтому команда не отображается. Используйте ExampleCommand в списке команд или измените имя целевого объекта на Example.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Сообщение: "Произошла ошибка при выполнении \<command name>. Не удалось получить команду \<target-name> из проекта".

Указывает, что содержимое элементов `<Target>` или `<CreatePythonCommandItem>` неправильно. Возможные причины:

- Обязательный атрибут `Target` пуст.
- Обязательный атрибут `TargetType` пуст или содержит неопознанное значение.
- Обязательный атрибут `ExecuteIn` пуст или содержит неопознанное значение.
- `ErrorRegex` или `WarningRegex` указан без задания `ExecuteIn="output"`.
- В элементе присутствуют неопознанные атрибуты. Например, вы могли использовать `Argumnets` (с опечаткой) вместо `Arguments`.

Значения атрибутов могут быть пустыми, если вы ссылаетесь на свойство, которое не было определено. Например, если вы используете токен `$(StartupFile)`, но в проекте не задан файл запуска, этот токен разрешается в пустую строку. В таких случаях может потребоваться определить значение по умолчанию. Например, команды **Запуск сервера** и **Запустить сервер отладки**, определенные в шаблонах проектов Bottle, Flask и Django, по умолчанию используют *manage.py*, если вы иным образом не указали файл запуска сервера в свойствах проекта.

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio перестает отвечать и аварийно завершает работу при выполнении команды

Скорее всего, вы пытаетесь запустить команду консоли с `ExecuteIn="output"`. В этом случае Visual Studio может аварийно завершить работу при попытке проанализировать выходные данные. Взамен рекомендуется использовать `ExecuteIn="console"`. (См. описание [запроса 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Исполняемая команда "не является внутренней или внешней командой, работающей программой или пакетным файлом"

При использовании `TargetType="executable"` значение в `Target` должно содержать *только* имя программы без аргументов, например только *python* или *python.exe*. Переместите все аргументы в атрибут `Arguments`.
