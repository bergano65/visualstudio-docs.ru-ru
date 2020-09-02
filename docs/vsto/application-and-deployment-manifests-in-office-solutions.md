---
title: Манифесты приложений и развертывания в решениях Office
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d22d58eb8a2264d5c7765a15726db556c7d5569f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62942906"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Манифесты приложений и развертывания в решениях Office
  Манифест приложения — это XML-файл, который содержит сведения, используемые решением Office для поиска и обновления своих сборок. Манифест приложения может использоваться с манифестом развертывания, представляющим собой XML-файл, который хранится на сервере и содержит сведения, необходимые для поиска самой последней версии манифеста приложения и сборок.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Структура манифеста для решений Office
 Для решений Microsoft Office, созданных с помощью средств разработки решений на базе Office в Visual Studio, все манифесты основаны на стандартной схеме ClickOnce. При развертывании решений Office манифесты приложений для проектов уровня документа и надстроек VSTO находятся в кэше ClickOnce. Манифесты развертывания не копируются на клиентский компьютер.

 Сведения о содержимом манифестов приложения и развертывания для проектов Office см. в статье [манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md) и [манифестов развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Создание манифестов приложения и развертывания
 Манифесты приложений создаются автоматически в процессе сборки. При каждой сборке проекта уровня документа расположение манифеста развертывания внедряется в документ в качестве пользовательского свойства документа. Для надстроек VSTO расположение манифеста развертывания хранится в реестре.

 Дополнительные сведения о **мастере публикации**см. в статье [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Дополнительные сведения о работе манифестов с решениями Office см. в статье [развертывание решения](../vsto/deploying-an-office-solution.md)Office.

## <a name="see-also"></a>См. также раздел

- [Архитектура настроек уровня документа](../vsto/architecture-of-document-level-customizations.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Манифесты приложений для решений Office](../vsto/application-manifests-for-office-solutions.md)
- [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)