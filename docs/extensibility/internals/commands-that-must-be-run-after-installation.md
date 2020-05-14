---
title: Команды, которые должны быть запущены после установки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709471"
---
# <a name="commands-that-must-be-run-after-installation"></a>Команды, которые должны быть запущены после установки
Если вы развернете расширение через файл *.msi,* вы должны запустить **devenv /настройка** как часть установки для того, чтобы Visual Studio обнаружила ваши расширения.

> [!NOTE]
> Информация в этой теме относится к поиску *devenv.exe* с Visual Studio 2008 и ранее. Для получения информации о том, как обнаружить *devenv.exe* с более поздними версиями Visual Studio, [см.](../../extensibility/internals/detecting-system-requirements.md)

## <a name="find-devenvexe"></a>Найти devenv.exe
 Вы можете найти *devenv.exe* каждой версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] из значений реестра, которые пишут установщики, используя таблицу RegLocator и таблицы AppSearch для хранения значений реестра в качестве свойств. Для получения дополнительной информации [см.](../../extensibility/internals/detecting-system-requirements.md)

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator строки таблицы, чтобы найти devenv.exe из различных версий Visual Studio

|Сигнатура|Root|Клавиши|name|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ-Microsoft-VisualStudio-7.0 -Установка|Окружающая средаПат|2|
|RL_DevenvExe_2003|2|ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ-Microsoft-VisualStudio-7.1 -Setup-VS|Окружающая средаПат|2|
|RL_DevenvExe_2005|2|ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ-Microsoft-VisualStudio-8.0 -Установка|Окружающая средаПат|2|
|RL_DevenvExe_2008|2|ПРОГРАММНОЕ ОБЕСПЕЧЕНИЕ-Microsoft-VisualStudio-9.0 -Установка|Окружающая средаПат|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Строки таблицы AppSearch для соответствующих строк таблицы RegLocator

|Свойство|Сигнатура|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Например, установщик Visual Studio записывает значение реестра **HKEY_LOCAL_MACHINE»-SOFTWARE-Microsoft-VisualStudio-9.0-Setup-VS-EnvironmentPath** как *C: 'VS2008-Common7-IDE-devenv.exe*, полный путь к исполняемой установке должен работать.

> [!NOTE]
> Поскольку столбец таблицы RegLocator составляет 2, нет необходимости указывать дополнительную информацию о версии в таблице Подписи.

## <a name="run-devenvexe"></a>Выполнить devenv.exe
 После запуска стандартного действия AppSearch в установщике каждое свойство в таблице AppSearch имеет значение, указавщее на файл *devenv.exe* для соответствующей версии Visual Studio. Если какой-либо из указанных значений реестра не присутствует - потому что эта версия Visual Studio не установлена - указанное свойство устанавливается в нулевые.

 Установка Windows поддерживает запуск исполняемого, к которому свойство указывает через пользовательский тип действия 50. Пользовательское действие должно включать параметры выполнения `msidbCustomActionTypeInScript` в скриптах `msidbCustomActionTypeCommit` (1024) и (512), чтобы гарантировать, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]что VSPackage был успешно установлен перед его интеграцией в. Для получения дополнительной информации смотрите [таблицу CustomAction](/windows/desktop/msi/customaction-table) и [параметры пользовательских действий в скрипте.](/windows/desktop/msi/custom-action-in-script-execution-options)

 Пользовательские действия типа 50 определяют свойство, содержащее исполняемое, как значение столбца «Источник» и аргументов командной строки в столбце Целевой.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Строки таблицы CustomAction для запуска devenv.exe

|Действие|Type|Источник|Назначение|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Установка|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Установка|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Установка|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Установка|

 Пользовательские действия должны быть замыканы в таблице InstallExecuteSequence, чтобы запланировать их для выполнения во время установки. Используйте соответствующее свойство в каждой строке столбца состояния, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предотвратить запуск пользовательского действия, если эта версия не установлена в системе.

> [!NOTE]
> Свойства, оцененные `False` по нулю, оцениваются при использовании в условиях.

 Значение столбца Sequence для каждого пользовательского действия зависит от других значений последовательности в пакете установки Windows. Значения последовательности должны быть такими, чтобы пользовательские действия *devenv.exe* запускались как можно ближе к стандартному действию InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>УстановкаТаблицаExecuteSequence для планирования пользовательских действий devenv.exe

|Действие|Условие|Последовательность|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>См. также
- [Установка VSPackages с установкой Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
