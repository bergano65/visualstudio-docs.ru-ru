---
title: Общие сведения о модели автоматизации | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdce23e892fe2fa14dc7f24f95d5744be2c67c39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562441"
---
# <a name="automation-model-overview"></a>Общие сведения о модели автоматизации
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Общие сведения о модели автоматизации](https://docs.microsoft.com/visualstudio/extensibility/internals/automation-model-overview).  
  
Модель автоматизации состоит из набора объектов, для которых можно написать надстройки Visual Studio или расширения. Надстройка — это приложение, можно управлять в среду Visual Studio и автоматизации общих задач. Расширение Visual Studio можно создавать пользовательские компоненты Visual Studio или добавить функциональные возможности стандартных компонентов, таких как текстовый редактор.  
  
## <a name="objects-in-the-automation-model"></a>Объекты в модели автоматизации  
 Модель автоматизации состоит из связанные группы объектов, которые управляют важнейшими областями среде. Ниже приведен схему, показывающую широкий набор объектов, из которых состоит модель автоматизации.  
  
 ![Таблица объекта анимации Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Объекты автоматизации Visual Studio  
  
 Дополнительные сведения см. в разделе [расширение среды Visual Studio](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 Среда предоставляет модель для различных функциональных областей. Например имеется модель кода для различных элементов, которые могут оказаться в коде. Имеется модель документа для различных элементов документа. Одной области, области проекта представляет интерес к поставщикам VSPackage. Вероятно, стоит на новых типов проектов, добавляемого в модели автоматизации так же, как [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] участвовать в модели автоматизации. Что процесс описан по [предоставление автоматизации для пакетов VSPackage](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Места, где можно рассмотреть расширение модели автоматизации среды:  
  
-   Проект  
  
-   Document  
  
-   Код  
  
-   Построить  
  
 Дополнительные сведения об автоматизации см. в разделе [Автоматизация и расширение среды для Visual Studio](http://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). В этом документе и документы также предоставляет ссылки на, помогают принимать решения о том, как следует предоставить автоматизации для VSPackage.  
  
## <a name="see-also"></a>См. также  
 [Практическое: создание надстройки](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)

