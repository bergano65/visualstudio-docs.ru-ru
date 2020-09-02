---
title: Представления последовательных рабочих процессов (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846213"
---
# <a name="sequential-workflow-views-legacy"></a>Представления последовательных рабочих процессов (для прежних версий)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] предоставляет устаревшую [!INCLUDE[wfd1](../includes/wfd1-md.md)] платформу, которая может использоваться для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] предоставляет способ создания с помощью графических средств приложений [!INCLUDE[wf](../includes/wf-md.md)] с использованием знакомого пользовательского интерфейса [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Приложения [!INCLUDE[wf](../includes/wf-md.md)] состоят из этапов рабочего процесса, называемых действиями. Чтобы создать рабочий процесс, создайте действия в области конструктора, перетащив соответствующие конструкторы действий из **области элементов** в область конструктора.

 При создании последовательного рабочего процесса, который является [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx), доступны три представления рабочего процесса. Эти представления доступны из меню **Рабочий процесс** и из контекстного меню в области конструктора.

 В следующей таблице перечислены имена и описание каждого представления.

|Параметры меню/вкладок|Описание|
|----------------------|-----------------|
|**Представление SequentialWorkflow**|Щелкните правой кнопкой мыши область конструктора и выберите в контекстном меню пункт **Просмотреть SequentialWorkflow** , чтобы отобразить представление **последовательного рабочего процесса** , которое показывает графическое представление последовательного рабочего процесса на основе действий. Или выберите **Просмотреть SequentialWorkflow** в меню **Рабочий процесс** .|
|**Просмотр обработчика отмены**|Щелкните правой кнопкой мыши область конструктора и выберите в контекстном меню пункт **Просмотреть обработчик отмены** , чтобы отобразить представление **последовательного рабочего процесса** , в котором отображается действие [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) , связанное с рабочим процессом. Или выберите **Просмотреть обработчик отмены** в меню **Рабочий процесс** .|
|**Просмотр обработчика ошибок**|Щелкните правой кнопкой мыши область конструктора и выберите в контекстном меню пункт **Просмотреть обработчик ошибок** , чтобы отобразить представление **ошибок** , в котором отображается действие [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) , связанное с рабочим процессом. Или выберите пункт **Просмотреть обработчик ошибок** в меню **Рабочий процесс** .|

 Дополнительные сведения о схожих представлениях см. в разделе [представления действий (прежние версии)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>См. также:
 [Представления действий (прежние версии)](../workflow-designer/activity-views-legacy.md) [Создание устаревших проектов рабочих](../workflow-designer/creating-legacy-workflow-projects.md) процессов. [режимы разработки рабочих процессов](https://msdn2.microsoft.com/library/bb628440.aspx)
