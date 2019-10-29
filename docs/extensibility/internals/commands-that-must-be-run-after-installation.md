---
title: Команды, которые должны быть выполнены после установки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982023"
---
# <a name="commands-that-must-be-run-after-installation"></a>Команды, которые должны быть выполнены после установки
При развертывании расширения с помощью *MSI* -файла необходимо запустить команду **devenv/setup** в процессе установки, чтобы Visual Studio обнаружила свои расширения.

> [!NOTE]
> Сведения в этом разделе относятся к поиску *файла devenv. exe* в Visual Studio 2008 и более ранних версий. Сведения о том, как обнаружить *файл devenv. exe* с более поздними версиями Visual Studio, см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Найти файл devenv. exe
 Вы можете разместить *файл devenv. exe* для каждой версии из значений реестра, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] записывать установщики, используя таблицу реглокатор и таблицы аппсеарч для хранения значений реестра в качестве свойств. Дополнительные сведения см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Реглокатор строки таблицы, чтобы открыть файл devenv. exe из разных версий Visual Studio

|Подпись|Корневой|Раздел|Название|Type|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|енвиронментпас|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|енвиронментпас|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|енвиронментпас|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|енвиронментпас|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Аппсеарч строки таблицы для соответствующих строк таблицы Реглокатор

|свойство;|Подпись|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Например, установщик Visual Studio записывает значение реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** как *C:\VS2008\Common7\IDE\devenv.exe*, полный путь к исполняемому файлу Установщик должен запуститься.

> [!NOTE]
> Так как столбец типа таблицы Реглокатор имеет значение 2, необязательно указывать дополнительные сведения о версии в таблице сигнатур.

## <a name="run-devenvexe"></a>Запуск devenv. exe
 После выполнения стандартного действия Аппсеарч в установщике каждое свойство в таблице Аппсеарч имеет значение, указывающее на файл *devenv. exe* для соответствующей версии Visual Studio. Если какие-либо из указанных значений реестра отсутствуют, так как эта версия Visual Studio не установлена, для указанного свойства устанавливается значение null.

 Установщик Windows поддерживает запуск исполняемого файла, на который указывает свойство через тип настраиваемого действия 50. Пользовательское действие должно включать в скрипт параметры выполнения, `msidbCustomActionTypeInScript` (1024) и `msidbCustomActionTypeCommit` (512), чтобы убедиться, что пакет VSPackage успешно установлен, прежде чем интегрировать его в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в статьях [Таблица CustomAction](/windows/desktop/msi/customaction-table) и [настраиваемое действие в параметрах выполнения в скрипте](/windows/desktop/msi/custom-action-in-script-execution-options).

 Пользовательские действия типа 50 указывают свойство, содержащее исполняемый файл, в качестве значения исходного столбца и аргументов командной строки в целевом столбце.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Строки таблицы CustomAction для запуска devenv. exe

|Действие|Type|Source|Target|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Пользовательские действия должны быть созданы в таблице Инсталлексекутесекуенце, чтобы запланировать их выполнение во время установки. Используйте соответствующее свойство в каждой строке столбца Condition, чтобы предотвратить запуск настраиваемого действия, если эта версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не установлена в системе.

> [!NOTE]
> Свойства со значением NULL оцениваются как `False` при использовании в условиях.

 Значение столбца последовательности для каждого настраиваемого действия зависит от других значений последовательности в пакете установщик Windows. Значения последовательности должны быть таким образом, чтобы настраиваемые действия *devenv. exe* выполнялись как можно ближе, прежде чем стандартное действие функции InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Инсталлексекутесекуенце таблица для планирования настраиваемых действий devenv. exe

|Действие|Условие|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)