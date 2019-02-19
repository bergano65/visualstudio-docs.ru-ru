---
title: Использование нескольких процессоров при сборке проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3ab8f3896c0a57657966c022f85c7827fedf3d65
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54792857"
---
# <a name="using-multiple-processors-to-build-projects"></a>Использование нескольких процессоров при построении проектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
В MSBuild реализована поддержка систем с несколькими процессорами или многоядерными процессорами. Для каждого доступного процессора создается отдельный процесс сборки. Например, если в системе есть четыре процессора, создается четыре процесса сборки. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может обрабатывать эти сборки одновременно, что позволяет сократить продолжительность операции. При этом параллельная сборка несколько изменяет процедуру выполнения процессов сборки. Такие изменения и рассматриваются в этой статье.  
  
## <a name="project-to-project-references"></a>Перекрестные ссылки между проектами  
 Если при использовании параллельной сборки [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] встречает ссылки проектов на проекты (P2P), ссылка создается только один раз. Если два проекта имеют одинаковые ссылки P2P, они не будут повторно создаваться отдельно для каждого проекта. Вместо этого обработчик сборки возвращает одну и ту же ссылку P2P обоим проектам, которые зависят от нее. В рамках сеанса все последующие запросы для одного целевого объекта возвращают одну и ту же ссылку P2P.  
  
## <a name="cycle-detection"></a>Обнаружение циклов  
 Обнаружение циклов работает так же, как и в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, — только теперь [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] может обнаруживать циклы в другое время или в ходе сборки.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Ошибки и исключения при параллельной сборке  
 В сравнении с непараллельной сборкой в ходе параллельной ошибки и исключения могут появляться в другие моменты времени. Если сборка одного проекта завершится неудачей, сборка других проектов продолжится. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] не останавливает сборку проектов, которые создаются параллельно с теми, сборка которых не удалась. Сборка других проектов будет продолжаться, пока не завершится успехом или ошибкой. Однако, если включено свойство <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, сборки не останавливаются даже при появлении ошибок.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Файлы решений (SLN-файлы) и проектов (VCPROJ-файлы) Visual C++  
 [Задача MSBuild](../msbuild/msbuild-task.md) может принимать файлы решений (SLN-файлы) и проектов (VCPROJ-файлы) [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. Для проектов [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] вызывается VCWrapperProject, а затем создается внутренний проект [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Для решений [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] вызывается SolutionWrapperProject, а затем создается внутренний проект [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. В обоих случаях полученный проект обрабатывается так же, как любой другой проект [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="multi-process-execution"></a>Выполнение нескольких процессов  
 Почти для всех действий, связанных со сборкой важно, чтобы текущий каталог оставался неизменным на протяжении всего процесса. Это позволяет избежать ошибок, связанных с правильностью путей. Как следствие, проекты нельзя выполнять в разных потоках [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], так как они будут создавать несколько каталогов.  
  
 Чтобы эта особенность позволяла использовать несколько процессоров для сборки, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] прибегает к изоляции процессов. Изоляция процессов позволяет [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] создавать вплоть до `n` процессов, где `n` равно числу процессоров, доступных в системе. Например если [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] собирает решение в системе с двумя процессорами, он создает только два процесса сборки. Эти процессы используются многократно для сборки всех проектов, входящих в решение.  
  
## <a name="see-also"></a>См. также раздел  
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  (Параллельная сборка нескольких проектов)  
 [Задачи](../msbuild/msbuild-tasks.md)
