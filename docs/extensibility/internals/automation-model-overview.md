---
title: Общие сведения о модели автоматизации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65698c140647831ab329069e61e2cc5ea826d6e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992117"
---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
Модель автоматизации состоит из набора объектов, для которых можно написать надстройки Visual Studio или расширения. Надстройка — это приложение, можно управлять в среду Visual Studio и автоматизации общих задач. Расширение Visual Studio можно создавать пользовательские компоненты Visual Studio или добавить функциональные возможности стандартных компонентов, таких как текстовый редактор.  
  
## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации  
 Модель автоматизации состоит из связанные группы объектов, которые управляют важнейшими областями среде. В примере ниже показан широкий набор объектов Visual Studio, из которых состоит модель автоматизации.  
  
 ![Таблица объекта анимации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
  
 Дополнительные сведения см. в разделе [расширения среды Visual Studio](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Среда предоставляет модель для различных функциональных областей. Например имеется модель кода для различных элементов, которые могут оказаться в коде. Имеется модель документа для различных элементов документа. Одной области, области проекта представляет интерес к поставщикам VSPackage. Вероятно, стоит на новых типов проектов, добавляемого в модели автоматизации так же, как [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] участвовать в модели автоматизации. Что процесс описан по [обеспечивают автоматизацию для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Места, где можно рассмотреть расширение модели автоматизации среды:  
  
-   Проект  
  
-   Document  
  
-   Код  
  
-   Построить  

  
Дополнительные сведения об автоматизации см. в разделе [Автоматизация и расширение среды для Visual Studio](../extensibility-in-visual-studio.md). В этом документе и документы также предоставляет ссылки на, помогают принимать решения о том, как следует предоставить автоматизации для VSPackage.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание надстройки](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)