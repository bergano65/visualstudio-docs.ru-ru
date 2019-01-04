---
title: Манифесты приложения и развертывания в решениях Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 24650d2cb4cbed3a5b4c4f1ee02e395e7b8c2988
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828566"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Манифесты приложения и развертывания в решениях Office
  Манифест приложения — это XML-файл, который содержит сведения, используемые решением Office для поиска и обновления своих сборок. Манифест приложения может использоваться с манифестом развертывания, представляющим собой XML-файл, который хранится на сервере и содержит сведения, необходимые для поиска самой последней версии манифеста приложения и сборок.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Структура манифеста для решений Office
 Для решений Microsoft Office, созданных с помощью средств разработки решений на базе Office в Visual Studio, все манифесты основаны на стандартной схеме ClickOnce. При развертывании решений Office манифесты приложений для проектов уровня документа и надстроек VSTO находятся в кэше ClickOnce. Манифесты развертывания не копируются на клиентский компьютер.

 Дополнительные сведения о содержимом манифестов приложения и развертывания для проектов Office, см. в разделе [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md) и [манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Создание манифестов приложения и развертывания
 Манифесты приложений создаются автоматически в процессе сборки. При каждой сборке проекта уровня документа расположение манифеста развертывания внедряется в документ в качестве пользовательского свойства документа. Для надстроек VSTO расположение манифеста развертывания хранится в реестре.

 Дополнительные сведения о **мастера публикации**, см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Дополнительные сведения о том, как манифесты работают с решениями Office, см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>См. также

- [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)
- [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)