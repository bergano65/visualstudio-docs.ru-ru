---
title: "Манифесты приложений и развертывания в решениях Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 83bf3b48d562e5acf24fedd27954c10505454b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Манифесты приложения и развертывания в решениях Office
  Манифест приложения — это XML-файл, который содержит сведения, используемые решением Office для поиска и обновления своих сборок. Манифест приложения может использоваться с манифестом развертывания, представляющим собой XML-файл, который хранится на сервере и содержит сведения, необходимые для поиска самой последней версии манифеста приложения и сборок.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Структура манифеста для решений Office  
 Для решений Microsoft Office, созданных с помощью средств разработки решений на базе Office в Visual Studio, все манифесты основаны на стандартной схеме ClickOnce. При развертывании решений Office манифесты приложений для проектов уровня документа и надстроек VSTO находятся в кэше ClickOnce. Манифесты развертывания не копируются на клиентский компьютер.  
  
 Сведения о содержимом манифестов приложений и развертывания для проектов Office см. в разделах [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md) и [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="creating-application-and-deployment-manifests"></a>Создание манифестов приложения и развертывания  
 Манифесты приложений создаются автоматически в процессе сборки. При каждой сборке проекта уровня документа расположение манифеста развертывания внедряется в документ в качестве пользовательского свойства документа. Для надстроек VSTO расположение манифеста развертывания хранится в реестре.  
  
 Дополнительные сведения о **мастер публикации**, в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Дополнительные сведения о том, как манифесты работают с решениями Office, см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Манифест развертывания ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  