---
title: Получение журналов построения с помощью MSBuild | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842513"
---
# <a name="obtaining-build-logs-with-msbuild"></a>Получение журналов построения с помощью MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью параметров MSBuild можно указать объем данных сборки для проверки и необходимость сохранения данных сборки в один или несколько файлов. Можно также указать пользовательское средство ведения журналов для сбора данных сборки. Сведения о параметрах командной строки MSBuild, которые не рассматриваются в этом разделе, см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> При сборке проектов с помощью интегрированной среды разработки Visual Studio для поиска и устранения неполадок сборок можно использовать журналы сборок. Дополнительные сведения см. в разделе [Практическое руководство. Просмотр, сохранение и настройка файлов журнала сборки](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Задание уровня детализации  
 При сборке проекта с помощью MSBuild без указания уровня детализации в выходном журнале отображаются следующие сведения:  
  
- ошибки, предупреждения и сообщения с высокой важностью;  
  
- некоторые события состояния;  
  
- сводка сборки.  
  
  С помощью параметра **/verbosity** (**/v**) можно управлять объемом данных, отображаемых в выходном журнале. Для устранения неполадок используйте уровень детализации `detailed` (`d`) или `diagnostic` (`diag`), который предоставляет максимум информации.  
  
  Процесс сборки может быть медленнее при установке параметра **/verbosity** в значение `detailed` и даже медленнее при установке **/verbosity** в значение `diagnostic` .  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>Сохранение журнала построения в файл  
 Для сохранения данных сборки в файл можно использовать параметр **/филелогжер** (**FL**). В следующем примере данные сборки сохраняются в файл с именем `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 В следующем примере файлу журнала присвоено имя `MyProjectOutput.log`, а уровень детализации выходных данных журнала задан как `diagnostic`. Эти два параметра указываются с помощью параметра **/филелогпараметерс** ( `flp` ).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Дополнительные сведения см. в разделе [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Сохранение выходных данных журнала в нескольких файлах  
 В следующем примере весь журнал сохраняется в `msbuild1.log`, только ошибки — в `JustErrors.log` и только предупреждения — в `JustWarnings.log`. В примере используется номера файлов для каждого из трех файлов. Номера файлов указываются сразу после параметров **/ФЛ** и **/FLP** (например, `/fl1` и `/flp1` ).  
  
 Параметры **/филелогпараметерс** ( `flp` ) для файлов 2 и 3 указывают, что следует присвоить каждому файлу имя и что следует включать в каждый файл. Для файла 1 имя не указано, поэтому используется имя по умолчанию — `msbuild1.log`.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Дополнительные сведения см. в разделе [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="using-a-custom-logger"></a>Использование пользовательского средства ведения журнала  
 Для создания собственного средства ведения журнала можно разработать управляемый тип, реализующий интерфейс <xref:Microsoft.Build.Framework.ILogger>. Пользовательское средство ведения журнала можно использовать, например для отправке ошибок сборки по электронной почте, регистрации их в базе данных или в XML-файл журнала. Дополнительные сведения см. в разделе [средства ведения журнала сборки](../msbuild/build-loggers.md).  
  
 В командной строке MSBuild укажите пользовательское средство ведения журнала с помощью параметра **/Logger** . Можно также использовать параметр **/noconsolelogger** , чтобы отключить средство ведения журнала консоли по умолчанию.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Средства ведения журнала сборки](../msbuild/build-loggers.md)   
 [Ведение журнала в многопроцессорной среде](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Создание средств ведения журнала переадресации](../msbuild/creating-forwarding-loggers.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
