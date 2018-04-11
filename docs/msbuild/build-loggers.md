---
title: Средства ведения журнала сборки | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 11
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d059cd9b9b108d9feba4c3878a3efc42c4f1403c
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/10/2018
---
# <a name="build-loggers"></a>Средства ведения журнала построения
Средства ведения журнала позволяют настраивать выходные данные сборки и отображать сообщения, ошибки или предупреждения в ответ на определенные события сборки. Каждое средство ведения журнала существует в виде класса .NET, который реализует интерфейс <xref:Microsoft.Build.Framework.ILogger>, определенный в сборке Microsoft.Build.Framework.dll.  
  
 Для средства ведения журнала можно использовать два подхода к реализации:  
  
-   Прямая реализация интерфейса <xref:Microsoft.Build.Framework.ILogger>.  
  
-   Наследование класса от вспомогательного класса <xref:Microsoft.Build.Utilities.Logger>, который определен в сборке Microsoft.Build.Utilities.dll. <xref:Microsoft.Build.Utilities.Logger> реализует <xref:Microsoft.Build.Framework.ILogger> и предоставляет реализацию по умолчанию некоторых элементов <xref:Microsoft.Build.Framework.ILogger>.  
  
 В этой статье мы расскажем, как создать простое средство ведения журнала, унаследованное от <xref:Microsoft.Build.Utilities.Logger>, которое отображает в консоли сообщения в ответ на определенные события сборки.  
  
## <a name="registering-for-events"></a>Регистрация в событиях  
 Средство ведения журнала предназначено для сбора сведений о выполнении сборки, которые поступает от обработчика сборки, и для представления этой информации в полезном формате. Все средства ведения журнала должны переопределять метод <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>, в котором средство ведения журнала регистрируется для событий. В этом примере средство ведения журнала регистрируется для событий <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> и <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="responding-to-events"></a>Реагирование на события  
 Теперь, когда средство ведения журнала зарегистрировано для определенных событий, оно будет обрабатывать эти события при их возникновении. Для событий <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> и <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> средство ведения журнала просто записывает короткую фразу и имя файла проекта, связанного с событием. Все сообщения из средства ведения журнала записываются в окно консоли.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Реагирование на значения детализации для средства ведения журнала  
 В некоторых случаях информацию о событии нужно записывать, только если параметр **/verbosity** для MSBuild.exe содержит определенное значение. В этом примере обработчик событий <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> записывает сообщение, только если свойство <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>, которое задается параметром **/verbosity** переключения, равно <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specifying-a-logger"></a>Выбор средства ведения журнала  
 Когда средство ведения журнала скомпилировано в сборку, нужно передать в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] информацию о том, что это средство ведения журнала следует использовать во время сборки. Для этого используйте параметр **/logger** для MSBuild.exe. Дополнительные сведения о доступных параметрах MSBuild.exe см. в [справочнике по командной строке](../msbuild/msbuild-command-line-reference.md).  
  
 Следующая команда выполняет сборку проекта `MyProject.csproj` с использованием класса ведения журнала, который реализован в `SimpleLogger.dll`. Параметр **/nologo** позволяет скрыть баннер и сообщение об авторских правах, а параметр **/noconsolelogger** отключает используемое по умолчанию консольное средство ведения журнала [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Следующая командная строка выполняет сборку проекта с тем же средством ведения журнала, но уже с уровнем `Verbosity` для `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере приведен полный код средства ведения журнала.  
  
### <a name="code"></a>Код  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
### <a name="comments"></a>Комментарии  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показано, как реализовать средство ведения журнала, которое записывает журнал в файл, а не окно консоли.  
  
### <a name="code"></a>Код  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
### <a name="comments"></a>Комментарии  
  
## <a name="see-also"></a>См. также  
 [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)