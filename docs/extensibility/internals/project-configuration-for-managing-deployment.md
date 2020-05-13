---
title: Конфигурация проекта для управления развертыванием Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706702"
---
# <a name="project-configuration-for-managing-deployment"></a>Конфигурация проекта для управления развертыванием
Развертывание — это акт физического перемещения выходных элементов из процесса сборки в ожидаемое место для отладки и установки. Например, веб-приложение может быть построено на локальной машине, а затем размещено на сервере.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поддерживает два способа вовлечения проектов в развертывание:

- Как предмет процесса развертывания.

- Как менеджер процесса развертывания.

  Прежде чем решения могут быть развернуты, необходимо сначала добавить проект развертывания для настройки вариантов развертывания. Если проект развертывания еще не существует, вас спрашивают, хотите ли вы создать его, когда вы выбираете **решение Deploy** из меню **сборки** или нажмите правой кнопкой мыши. Нажатие **Да** открывает диалоговую коробку **Add New Project** с выбранным проектом Remote Deploy **Wizard.**

  Мастер удаленного развертывания запрашивает тип приложения (Windows или Web), группы вывода проектов, любые дополнительные файлы, которые вы хотите включить, и удаленный компьютер, который вы хотите развернуть. На последней странице мастера отображается резюме выбранных вариантов.

  Проекты, которые являются предметом процесса развертывания, создают выходные элементы, которые должны быть перемещены в альтернативную среду. Эти выходные элементы описываются <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> как параметры интерфейса, основная цель которых, если позволить проектам группировать выходы. Для получения дополнительной информации, касающейся реализации, `IVsProjectCfg2`см. [Project Configuration for Output](../../extensibility/internals/project-configuration-for-output.md)

  Проекты развертывания, которые управляют процессом развертывания, позволяют командовать развертывание и отвечать при выборе этой команды. Проекты развертывания <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> реализуют интерфейс для выполнения <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> развертывания и делают звонки в интерфейс для сообщения о событиях состояния развертывания.

  Конфигурации могут указывать зависимости, влияющие на их операции сборки или развертывания. Создание или развертывание зависимостей являются проектами, которые должны быть построены или развернуты до или после самих конфигураций построены или развернуты. Создание зависимостей между проектами <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> описывается с интерфейсом и развертывает зависимости с интерфейсом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> Для получения дополнительной информации [см.](../../extensibility/internals/project-configuration-for-building.md)

## <a name="see-also"></a>См. также
- [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md)
- [Конфигурация проекта для сборки](../../extensibility/internals/project-configuration-for-building.md)
- [Конфигурация проекта для вывода](../../extensibility/internals/project-configuration-for-output.md)
