---
title: Команды, которые должны быть выполнены после установки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843145"
---
# <a name="commands-that-must-be-run-after-installation"></a>Команды, которые необходимо выполнить после установки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При развертывании расширения с помощью MSI-файла необходимо выполнить в `devenv /setup` процессе установки, чтобы Visual Studio обнаружил расширения.  
  
> [!NOTE]
> Сведения в этом разделе относятся к поиску DevEnv с Visual Studio 2008 и более ранних версий. Сведения об обнаружении команды DevEnv с более поздними версиями Visual Studio см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Поиск devenv.exe  
 devenv.exe каждой версии можно узнать из значений реестра, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] записываемых установщиками, используя таблицу реглокатор и таблицу аппсеарч для хранения значений реестра в качестве свойств. Дополнительные сведения см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Реглокатор строки таблицы для нахождение devenv.exe из разных версий Visual Studio  
  
|Signature_|Root|Клавиши|Название|Тип|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|енвиронментпас|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|енвиронментпас|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|енвиронментпас|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|енвиронментпас|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Аппсеарч строки таблицы для соответствующих строк таблицы Реглокатор  
  
|Свойство|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Например, установщик Visual Studio записывает значение реестра **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** как **C:\VS2008\Common7\IDE\devenv.exe**, полный путь к исполняемому файлу, который должен запустить установщик.  
  
 **Примечание** . Так как столбец типа Реглокатор имеет значение 2, необязательно указывать дополнительные сведения о версии в таблице сигнатур.  
  
## <a name="running-devenvexe"></a>Выполнение devenv.exe  
 После выполнения стандартного действия Аппсеарч в установщике каждое свойство в таблице Аппсеарч имеет значение, указывающее на файл devenv.exe для соответствующей версии Visual Studio. Если какие-либо из указанных значений реестра отсутствуют, так как эта версия Visual Studio не установлена, для указанного свойства устанавливается значение null.  
  
 Установщик Windows поддерживает запуск исполняемого файла, на который указывает свойство через тип настраиваемого действия 50. Настраиваемое действие должно включать в себя параметры выполнения в скрипте, Мсидбкустомактионтипеинскрипт (1024) и Мсидбкустомактионтипекоммит (512), чтобы убедиться, что пакет VSPackage успешно установлен перед интеграцией в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Дополнительные сведения см. в статьях таблица CustomAction и настраиваемое действие в параметрах выполнения в скрипте.  
  
 Пользовательские действия типа 50 указывают свойство, содержащее исполняемый файл, в качестве значения исходного столбца и аргументов командной строки в целевом столбце.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>Строки таблицы CustomAction для выполнения devenv.exe  
  
|Действие|Тип|Источник|Назначение|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Пользовательские действия должны быть созданы в таблице Инсталлексекутесекуенце, чтобы запланировать их выполнение во время установки. Используйте соответствующее свойство в каждой строке столбца Condition, чтобы предотвратить выполнение настраиваемого действия, если эта версия [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] не установлена в системе.  
  
> [!NOTE]
> `Null` Свойства оцениваются `False` при использовании в условиях.  
  
 Значение столбца последовательности для каждого настраиваемого действия зависит от других значений последовательности в пакете установщик Windows. Значения последовательности должны быть таким, чтобы devenv.exe настраиваемые действия запускаться как можно ближе, до выполнения стандартного действия функции InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Инсталлексекутесекуенце таблица для планирования devenv.exe настраиваемых действий  
  
|Действие|Условие|Sequence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>См. также:  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
