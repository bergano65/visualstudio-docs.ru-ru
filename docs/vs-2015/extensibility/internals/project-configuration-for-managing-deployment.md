---
title: Конфигурация проекта для управления развертыванием | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5b16c3392e9432ba540130d45f6907de15b51ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429955"
---
# <a name="project-configuration-for-managing-deployment"></a>Конфигурация проекта для управления развертыванием
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Развертывание — это процесс физического перемещения выходных элементов из процесса сборки в ожидаемое расположение для отладки и установки. Например, веб-приложение может быть построено на локальном компьютере, а затем помещено на сервер.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает два способа внедрения проектов в развертывание:  
  
- В качестве субъекта процесса развертывания.  
  
- В качестве руководителя процесса развертывания.  
  
  Перед развертыванием решений необходимо сначала добавить проект развертывания, чтобы настроить параметры развертывания. Если проект развертывания еще не существует, вам будет предложено создать его, выбрав пункт **Развернуть решение** в меню **Сборка** или щелкнув решение правой кнопкой мыши. При нажатии кнопки **Да** открывается диалоговое окно **Добавление нового проекта** с выбранным проектом **мастера удаленного развертывания** .  
  
  Мастер удаленного развертывания запрашивает тип приложения (Windows или веб), включаемые группы выходных данных проекта, любые дополнительные файлы, которые необходимо включить, и удаленный компьютер, на котором требуется выполнить развертывание. На последней странице мастера отображается сводка по выбранным параметрам.  
  
  Проекты, являющиеся субъектом процесса развертывания, создают выходные элементы, которые необходимо переместить в другую среду. Эти выходные элементы описаны в качестве параметров для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> интерфейса, основной целью которого является разрешение на группирование выходных данных в проектах. Дополнительные сведения о реализации `IVsProjectCfg2` см. в разделе [Конфигурация проекта для выходных данных](../../extensibility/internals/project-configuration-for-output.md).  
  
  Проекты развертывания, которые управляют процессом развертывания, включают команду deploy и отвечают, если выбрана эта команда. Проекты развертывания реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейс для выполнения развертывания и выполнения вызовов к <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> интерфейсу для сообщения о событиях состояния развертывания.  
  
  Конфигурации могут задавать зависимости, влияющие на операции сборки или развертывания. Сборки или развертывания зависимостей — это проекты, которые должны быть созданы или развернуты до или после построения или развертывания конфигураций. Сборки зависимостей между проектами описаны в <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> интерфейсе и развертывают зависимости с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> интерфейса. Дополнительные сведения см. в разделе [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>См. также:  
 [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)   
 [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)   
 [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)
