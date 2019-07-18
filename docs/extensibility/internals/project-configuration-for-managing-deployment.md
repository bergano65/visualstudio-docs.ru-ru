---
title: Конфигурации проекта для управления развертыванием | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8dfaf2f802a0470270c7630ccee3a8be583b250
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328455"
---
# <a name="project-configuration-for-managing-deployment"></a>Конфигурация проекта для управления развертыванием
Развертывание — это процесс физического перемещения выходных элементов из процесса сборки в правильное место для отладки и установки. Например веб-приложение может на локальном компьютере и затем размещаются на сервере.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает два способа, что проекты может потребоваться в развертывании:

- Как тема процесс развертывания.

- Как диспетчер процесса развертывания.

  Перед развертыванием решения, необходимо сначала добавить проект развертывания для настройки параметров развертывания. Развернуть проект еще не существует, появится необходимость создать его при выборе **развернуть решение** из **построения** меню или щелкните правой кнопкой мыши решение. Щелкнув **Да** открывает **Добавление нового проекта** диалоговое окно с **мастер удаленного развертывания** выбранный проект.

  Мастер удаленного развертывания предлагает для типа приложения (Windows или веб), группы выходных данных проекта для включения, дополнительные файлы, которые вы хотите включить и вы хотите развернуть на удаленном компьютере. Последней странице мастера отображает сводку выбранных параметров.

  Проекты, которые являются предметом процесс развертывания создают выходных элементов, которые необходимо переместить в другую среду. Эти выходные элементы описаны как параметры для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> интерфейс, в которых основной цели if позволить проектам группировать вывод. Дополнительные сведения, относящиеся к реализации `IVsProjectCfg2`, см. в разделе [конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md).

  Проекты развертывания, которые управляют процесс развертывания, включите команду развертывания и ответное действие при выборе этой команды. Проекты развертывания реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейс для выполнения развертывания и выполнения вызовов <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> интерфейс отчет развертывание события состояния.

  Конфигурации можно указать зависимости, которые повлияли на работу их сборки или развертывания. Постройте или разверните зависимости — это проект, необходимо либо быть сборки или развертывания до или после конфигураций, сами являются сборки или развертывания. Сборка зависимости между проектами, описаны в <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> интерфейс и развертывание зависимостей с <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> интерфейс. Дополнительные сведения см. в разделе [конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>См. также
- [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)
- [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)
- [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)