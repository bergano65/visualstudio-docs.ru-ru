---
title: "Манифесты приложения и развертывания в решениях Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "манифесты [разработка решений Office в Visual Studio]"
  - "манифесты развертывания [разработка решений Office в Visual Studio]"
  - "манифесты приложения [разработка решений Office в Visual Studio]"
  - "сборки [разработка решений Office в Visual Studio], обновление"
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Манифесты приложения и развертывания в решениях Office
  Манифест приложения — это XML\-файл, который содержит сведения, используемые решением Office для поиска и обновления своих сборок. Манифест приложения может использоваться с манифестом развертывания, представляющим собой XML\-файл, который хранится на сервере и содержит сведения, необходимые для поиска самой последней версии манифеста приложения и сборок.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Структура манифеста для решений Office  
 Для решений Microsoft Office, созданных с помощью средств разработки решений на базе Office в Visual Studio, все манифесты основаны на стандартной схеме ClickOnce. При развертывании решений Office манифесты приложений для проектов уровня документа и надстроек VSTO находятся в кэше ClickOnce. Манифесты развертывания не копируются на клиентский компьютер.  
  
 Сведения о содержимом манифестов приложений и развертывания для проектов Office см. в разделах [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md) и [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
## Создание манифестов приложения и развертывания  
 Манифесты приложений создаются автоматически в процессе сборки. При каждой сборке проекта уровня документа расположение манифеста развертывания внедряется в документ в качестве пользовательского свойства документа. Для надстроек VSTO расположение манифеста развертывания хранится в реестре.  
  
 Дополнительные сведения о **мастере публикации** см. в разделе [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Дополнительные сведения о том, как манифесты работают с решениями Office, см. в статье [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## См. также  
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)  
  
  