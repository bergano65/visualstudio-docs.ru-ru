---
title: "Команды, которые необходимо выполнить после установки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "После установки команды"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Команды, которые необходимо выполнить после установки
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При развертывании расширения через файл MSI необходимо запустить `devenv/setup` как часть установки чтобы обнаруживать расширений Visual Studio.  
  
> [!NOTE]
>  Сведения этого раздела применяются к поиск DevEnv в Visual Studio 2008 и более ранних версий. Сведения об обнаружении DevEnv с более поздними версиями Visual Studio см. в разделе [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).  
  
## Поиск devenv.exe  
 Каждой версии можно найти devenv.exe из реестра значения, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] записи установщиков, с использованием таблицы RegLocator и AppSearch таблицы для хранения значений реестра как свойства. Для получения дополнительной информации см. [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md).  
  
### RegLocator строки таблицы, чтобы найти devenv.exe из разных версий Visual Studio  
  
|Signature\_|Корень|Ключ|Имя|Тип|  
|-----------------|------------|----------|---------|---------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### Строки таблицы AppSearch для соответствующей строки таблицы RegLocator  
  
|Свойство|Signature\_|  
|--------------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 Например, установщик Visual Studio записывает значение реестра **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** как **C:\\VS2008\\Common7\\IDE\\devenv.exe**, полный путь к исполняемому файлу, необходимо запустить программу установки.  
  
 **Примечание** так как столбец типа RegLocator 2, не обязательно указывать дополнительные сведения о версии в таблице подписи.  
  
## Выполнение devenv.exe  
 После AppSearch, стандартное действие выполняется в установщик каждое свойство в таблице AppSearch имеет значение указывает на файл devenv.exe, соответствующую версии Visual Studio. Любые значения указанного реестра не существуют, поскольку этой версии Visual Studio не установлен — указанное свойство имеет значение значение null.  
  
 Установщик Windows поддерживает выполнения исполняемого объекта, на который указывает свойство с помощью настраиваемого действия введите 50. Настраиваемое действие должно включать в скрипт параметры выполнения, msidbCustomActionTypeInScript \(1024\) и msidbCustomActionTypeCommit \(512\), чтобы убедиться в успешной установке VSPackage до интеграции его в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе CustomAction таблицы и параметры выполнения пользовательского действия в скрипт.  
  
 Настраиваемые действия типа 50 указать свойство, содержащее исполняемый файл в качестве значения исходного столбца и аргументы командной строки в целевой столбец.  
  
### Строки таблицы настраиваемое действие для запуска devenv.exe  
  
|Действие|Тип|Исходный код|целевого объекта|  
|--------------|---------|------------------|----------------------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/ Setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/ Setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/ Setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/ Setup|  
  
 Настраиваемые действия должны быть авторизованы в таблицу InstallExecuteSequence, чтобы запланировать их выполнение во время установки. Используйте соответствующее свойство в каждой строке столбца условие для предотвращения настраиваемое действие, если запуск версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] не установлен в системе.  
  
> [!NOTE]
>  `Null` значение свойства `False` при использовании в условиях.  
  
 Значение столбца последовательности для каждого настраиваемого действия зависит от значений других последовательностей в пакет установщика Windows. Значения последовательности должны быть таким образом, что настраиваемые действия devenv.exe, запуск от имени близко к непосредственно перед стандартное действие функции installfinalize установок.  
  
### Таблица InstallExecuteSequence планирование devenv.exe настраиваемых действий  
  
|Действие|Условие|Sequence|  
|--------------|-------------|--------------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## См. также  
 [Установка пакетов VSPackages с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)