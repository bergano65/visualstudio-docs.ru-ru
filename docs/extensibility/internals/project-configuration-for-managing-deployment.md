---
title: "Конфигурации проекта для управления развертыванием | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87098c362e5b37690e2ab3116ffca431d58f129d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-managing-deployment"></a>Настройка проекта для управления развертыванием
Развертывание — это физического перемещения выходных элементов из процесс построения в правильное место для отладки и установки. Например веб-приложение может основаны на локальный компьютер и затем помещается на сервере.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поддерживает два способа задействуется проектов в развертывании.  
  
-   В строке темы процесс развертывания.  
  
-   Руководитель процесса развертывания.  
  
 Перед развертыванием решения, сначала необходимо добавить проект развертывания для настройки параметров развертывания. Если развернуть проект еще не существует, будет предложено, если вы хотите создать его при выборе **развернуть решение** из **построения** меню или щелкните правой кнопкой мыши решение. Щелкнув **Да** открывает **Добавление нового проекта** диалоговое окно с **мастер удаленного развертывания** выбранный проект.  
  
 Мастер удаленного развертывания предлагает для типа приложения (Windows или веб-узел), включаемые группы выходных данных проекта, все дополнительные файлы, которые необходимо включить и удаленного компьютера, который вы хотите развернуть. Последняя страница мастера отображается Сводка выбранных параметров.  
  
 Проекты, которые воздействуют процесса развертывания создают выходные элементы, которые требуется переместить в другую среду. Эти выходные элементы описаны как параметры для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> интерфейс, которого основной цели if разрешить проектов группы выходных данных. Дополнительные сведения, относящиеся к реализации `IVsProjectCfg2`, в разделе [конфигурации проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).  
  
 Проекты развертывания, в которых управлять процессом развертывания, включите команду развертывания и реагировать на них при выборе этой команды. Проекты развертывания реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейс для выполнения развертывания и выполнять вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> интерфейс отчет развертывание событий состояния.  
  
 Конфигурации можно задать зависимости, которые влияют на свои операции сборки или развертывания. Построение или развертывание проектов, которые должны быть построен или развернут до или после конфигурации сами построении и развертывании существуют зависимости. Построение зависимости между проектами, описаны в <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> интерфейса и развернуть зависимости с <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> интерфейса. Дополнительные сведения см. в разделе [конфигурации проекта для построения](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>См. также  
 [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)   
 [Настройка проекта для построения](../../extensibility/internals/project-configuration-for-building.md)   
 [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)