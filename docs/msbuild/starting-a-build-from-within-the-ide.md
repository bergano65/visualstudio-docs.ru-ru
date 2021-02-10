---
title: Запуск сборки из интегрированной среды разработки | Документы Майкрософт
description: Сведения о том, как с помощью Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor запускать сборки для пользовательских систем проектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ee685ebf542dbf9405afce8cfdf5c4a7e060b79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956052"
---
# <a name="start-a-build-from-within-the-ide"></a>Запуск построения из интегрированной среды разработки

Для запуска сборок пользовательские системы проектов должны использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor>. В этой статье описаны причины этого требования, а также соответствующая процедура.

## <a name="parallel-builds-and-threads"></a>Параллельные сборки и потоки

 Visual Studio позволяет использовать параллельные сборки, при выполнении которых необходим посредник для доступа к общим ресурсам. Системы проектов могут запускать сборки асинхронно, но такие системы не должны вызывать функции сборки из обратных вызовов.

 Если система проектов изменяет переменные среды, она должна присваивать NodeAffinity сборки значение OutOfProc. Это требование означает, что вы не можете использовать объекты узла, так как им требуется внутрипроцессный узел.

## <a name="use-ivsbuildmanageraccessor"></a>Использование IVSBuildManagerAccessor

 Следующий код описывает метод, который система проектов может использовать для запуска сборки:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```
