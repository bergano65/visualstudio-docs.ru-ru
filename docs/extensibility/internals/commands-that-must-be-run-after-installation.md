---
title: "Команды, которые необходимо выполнить после установки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4fef2c76364c1ca1398aef3b94226e7a9a365cf1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="commands-that-must-be-run-after-installation"></a>Команды, которые необходимо выполнить после установки
При развертывании расширения через файл MSI необходимо запустить `devenv /setup` как часть установки в порядке для Visual Studio для обнаружения расширений.  
  
> [!NOTE]
>  Информация в этом разделе относится к поиск DevEnv вместе с Visual Studio 2008 и более ранних версий. Сведения об обнаружении DevEnv с более поздними версиями Visual Studio см. в разделе [требования к системе для обнаружения](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Поиск devenv.exe  
 Каждой версии можно найти devenv.exe из реестра значения, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установщики записи с использованием таблицы RegLocator и AppSearch таблицы для хранения значений реестра как свойства. Дополнительные сведения см. в разделе [требования к системе для обнаружения](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator строк таблицы, чтобы найти devenv.exe из разных версий Visual Studio  
  
|Signature_|корень|Ключ|Имя|Тип|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Строки таблицы AppSearch для соответствующей строки таблицы RegLocator  
  
|Свойство|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Например, установщик Visual Studio записывает значение реестра **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** как **C:\VS2008\Common7\IDE\devenv.exe**, полный путь к исполняемому файлу, необходимо запустить программу установки.  
  
 **Примечание** так как столбец типа RegLocator 2, не требуется указывать дополнительные сведения о версии в таблице подписи.  
  
## <a name="running-devenvexe"></a>Под управлением devenv.exe  
 После AppSearch, стандартное действие выполняется в установщик каждое свойство в таблице AppSearch имеет значение файл devenv.exe для соответствующей версии Visual Studio. Присутствуют не все значения указанного раздела, так как этой версии Visual Studio не установлен, указанное свойство имеет значение в значение null.  
  
 Установщик Windows поддерживает запуск исполняемого файла, на который указывает свойство с помощью настраиваемого действия ввести число 50. Настраиваемое действие должен включать параметры выполнения в скрипт, msidbCustomActionTypeInScript (1024) и msidbCustomActionTypeCommit (512), для обеспечения успешной установки VSPackage перед его в интеграции [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе таблица настраиваемое действие и параметры выполнения пользовательского действия в скрипт.  
  
 Настраиваемые действия типа 50 указать свойство, содержащий исполняемый файл в качестве значения исходного столбца и аргументы командной строки в целевой столбец.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Строки таблицы настраиваемое действие для выполнения devenv.exe  
  
|Действие|Тип|Исходный код|целевого объекта|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/ Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/ Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/ Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/ Setup|  
  
 Настраиваемые действия должны быть авторизованы в таблицу InstallExecuteSequence необходимо запланировать их для выполнения во время установки. Использовать соответствующее свойство в каждой строке столбца условие для препятствующих пользовательские действия выполняются, если это версия [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не установлен в системе.  
  
> [!NOTE]
>  `Null`значение свойства `False` при использовании в условиях.  
  
 Значение столбца для каждого настраиваемого действия последовательности зависит от других значений последовательности в пакет установщика Windows. Значения последовательности должны быть таким образом, чтобы закрыть devenv.exe пользовательские действия запуска от имени можно ближе к непосредственно перед InstallFinalize стандартное действие.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Таблица InstallExecuteSequence планирование devenv.exe пользовательские действия  
  
|Действие|Условие|Sequence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>См. также  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)