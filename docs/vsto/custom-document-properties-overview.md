---
title: Общие сведения о свойствах пользовательского документа
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 11c344b683a67f369ef3848a41b7907622945ffa
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866861"
---
# <a name="custom-document-properties-overview"></a>Общие сведения о свойствах пользовательского документа

При сборке проекта уровня документа Visual Studio добавляет в документ в проекте двум настраиваемым свойствам: \_AssemblyLocation и \_AssemblyName. Когда пользователь открывает документ, приложение Microsoft Office проверяет наличие настраиваемых свойств документа. Если они существуют в документе, приложение загружает [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], которая запускает настройку. Дополнительные сведения см. в разделе [решений архитектура Microsoft Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_Имя_сборки

Это свойство содержит CLSID интерфейса в компоненте загрузчик решений Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Значение идентификатора CLSID — 4 4E3C66D5 - 58D-491E-A7D4-64AF99AF6E8B. Никогда не изменяйте это значение.

## <a name="assemblylocation"></a>\_AssemblyLocation

Это свойство содержит строку, которая предоставляет сведения о манифесте развертывания для настройки. Дополнительные сведения о манифестах см. в разделе [манифесты приложений и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 \_AssemblyLocation значение свойства могут иметь различные форматы, в зависимости от способа развертывания решения:

- Если решение публикуется устанавливаться с веб-сайта, UNC-путь или компакт-диска или USB-накопитель, свойства _AssemblyLocation имеет формат *DeploymentManifestPath*|*SolutionID*. Следующая строка представляет пример:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- При выполнении или отладке решения из Visual Studio, свойства _AssemblyLocation имеет формат *DeploymentManifestName*|*SolutionID*| vstolocal. Следующая строка представляет пример:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  *SolutionID* представляет собой идентификатор GUID, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] используется для идентификации решения. *SolutionID* создается автоматически при сборке проекта. **Vstolocal** условие указывает на [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] что сборка должна быть загружена из той же папке, что документ.

## <a name="see-also"></a>См. также

- [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)
- [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Практическое руководство. Публикация решения Office с помощью ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Практическое руководство. Создание и изменение настраиваемых свойств документа](../vsto/how-to-create-and-modify-custom-document-properties.md)
