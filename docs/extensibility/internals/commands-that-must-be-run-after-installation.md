---
title: Команды, которые должны выполняться после установки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d336e4a65178ff09f5db01dffeb5bedd3b5b946e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631397"
---
# <a name="commands-that-must-be-run-after-installation"></a>Команды, которые должны выполняться после установки
При развертывании расширения с помощью *.msi* файл, необходимо запустить **devenv/setup** как часть установки в порядке для Visual Studio для обнаружения расширений.

> [!NOTE]
>  Сведения этого раздела применяются к поиску *devenv.exe* с Visual Studio 2008 и более ранних версий. Сведения об обнаружении *devenv.exe* в более поздних версиях Visual Studio, см. в разделе [определить требования к системе](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Найти devenv.exe
 Вы можете найти каждой версии *devenv.exe* из реестра значения, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установщиков записывают, используя таблицу RegLocator и AppSearch таблицы для хранения значений реестра как свойства. Дополнительные сведения см. в разделе [определить требования к системе](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator строк таблицы, чтобы найти devenv.exe из разных версий Visual Studio

|Подпись|Корневой|Ключ|name|Тип|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Строки таблицы AppSearch соответствующих строк в таблицах RegLocator

|Свойство.|Подпись|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Например, установщик Visual Studio записывает значение реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** как *C:\VS2008\Common7\IDE\devenv.exe*, полный путь к исполняемому файлу, необходимо запустить программу установки.

> [!NOTE]
> Так как тип столбца в таблице RegLocator равно 2, не требуется указывать дополнительные сведения о версии в таблице подписи.

## <a name="run-devenvexe"></a>Запустите devenv.exe
 После AppSearch, стандартное действие выполняется в установщике, каждое свойство в таблице AppSearch имеет значение, указывающие на *devenv.exe* файл для соответствующей версией Visual Studio. Если какие-либо значения указанного раздела отсутствуют, так как эта версия Visual Studio не установлена — указанное свойство имеет значение значение null.

 Установщик Windows поддерживает запуска исполняемого файла, на который указывает свойство с помощью настраиваемого действия ввести число 50. Настраиваемое действие должно включать параметры выполнения в скрипт, `msidbCustomActionTypeInScript` (1024) и `msidbCustomActionTypeCommit` (512), чтобы убедиться в успешной установке VSPackage перед интеграцией в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [CustomAction таблицы](https://docs.microsoft.com/windows/desktop/msi/customaction-table) и [настраиваемые параметры выполнения сценария в действие](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options).

 Настраиваемые действия типа 50 задано свойство, содержащий исполняемый файл в качестве значения исходного столбца и аргументы командной строки в целевой столбец.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Строки таблицы настраиваемое действие для запуска devenv.exe

|Действие|Тип|Исходный код|целевого объекта|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|

 Настраиваемые действия должны быть авторизованы в таблицу InstallExecuteSequence запланировать их для выполнения во время установки. Использовать соответствующее свойство в каждой строке столбца условие для предотвращения настраиваемого действия из выполняются, если это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не установлен в системе.

> [!NOTE]
>  Свойства со значением NULL имеют значение `False` при использовании в условиях.

 Значение столбца последовательности для каждого пользовательского действия зависит от других значений последовательности, в пакет установщика Windows. Значения последовательности должны быть таким образом, чтобы *devenv.exe* настраиваемые действия, запуск от имени максимально близко к непосредственно перед стандартное действие функции installfinalize запущенных установок.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Таблица InstallExecuteSequence запланировать devenv.exe пользовательские действия

|Действие|Условие|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)