---
title: Получение журналов построения с помощью MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6953017a034257900c467e7f2fac89897fa0d9e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="obtaining-build-logs-with-msbuild"></a>Получение журналов построения с помощью MSBuild
С помощью параметров MSBuild можно указать объем данных сборки для проверки и необходимость сохранения данных сборки в один или несколько файлов. Можно также указать пользовательское средство ведения журналов для сбора данных сборки. Сведения о параметрах командной строки MSBuild, не рассматриваемых в этом разделе, см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  При сборке проектов с помощью интегрированной среды разработки Visual Studio для поиска и устранения неполадок сборок можно использовать журналы сборок. Дополнительные сведения см. в статье [Практическое руководство. Просмотр, сохранение и настройка файлов журнала сборки](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Задание уровня детализации  
 При сборке проекта с помощью MSBuild без указания уровня детализации в выходном журнале отображаются следующие сведения:  
  
-   ошибки, предупреждения и сообщения с высокой важностью;  
  
-   некоторые события состояния;  
  
-   сводка сборки.  
  
 Используя параметр **/verbosity** (**/v**), можно контролировать объем данных, отображаемых в журнале выходных данных. Для устранения неполадок используйте уровень детализации `detailed` (`d`) или `diagnostic` (`diag`), который предоставляет максимум информации.  
  
 Сборка может выполняться медленнее при задании для параметра **/verbosity** значения `detailed` и еще медленнее при задании для **/verbosity** значения `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  

## <a name="saving-the-build-log-to-a-file"></a>Сохранение журнала построения в файл  
 Параметр **/fileLogger** (**fl**) можно использовать для сохранения данных сборки в файл. В следующем примере данные сборки сохраняются в файл с именем `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 В следующем примере файлу журнала присвоено имя `MyProjectOutput.log`, а уровень детализации выходных данных журнала задан как `diagnostic`. Эти две настройки указываются с помощью параметра **/filelogparameters** (`flp`).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Дополнительные сведения см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Сохранение выходных данных журнала в нескольких файлах  
 В следующем примере весь журнал сохраняется в `msbuild1.log`, только ошибки — в `JustErrors.log` и только предупреждения — в `JustWarnings.log`. В примере используется номера файлов для каждого из трех файлов. Номер файлов указываются после параметров **/fl** и **/flp** (например, `/fl1` и `/flp1`).  
  
 Параметры **/filelogparameters** (`flp`) для файлов 2 и 3 указывают имя для каждого файла и компоненты, включаемые в каждый файл. Для файла 1 имя не указано, поэтому используется имя по умолчанию — `msbuild1.log`.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Дополнительные сведения см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  

## <a name="saving-a-binary-log"></a>Сохранение двоичного файла журнала

Чтобы сохранить журнал в сжатом двоичном формате, используйте параметр **/binaryLogger** (**bl**). Этот журнал содержит подробное описание процесса сборки и может считываться определенными средствами анализа журнала.

В следующем примере создается двоичный файл журнала с именем `binarylogfilename`.

```  
/bl:binarylogfilename.binlog
``` 
 
Дополнительные сведения см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  

## <a name="using-a-custom-logger"></a>Использование пользовательского средства ведения журнала  
 Для создания собственного средства ведения журнала можно разработать управляемый тип, реализующий интерфейс <xref:Microsoft.Build.Framework.ILogger>. Пользовательское средство ведения журнала можно использовать, например для отправке ошибок сборки по электронной почте, регистрации их в базе данных или в XML-файл журнала. Дополнительные сведения см. в разделе [Средства ведения журнала сборки](../msbuild/build-loggers.md).  
  
 В командной строке MSBuild укажите пользовательское средство ведения журнала с помощью параметра **/logger**. Можно также использовать параметр **/noconsolelogger**, чтобы отключить средство ведения журнала консоли по умолчанию.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Средства ведения журнала сборки](../msbuild/build-loggers.md)   
 [Ведение журнала в многопроцессорной среде](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Создание средств ведения журнала переадресации](../msbuild/creating-forwarding-loggers.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)