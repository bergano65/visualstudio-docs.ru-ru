---
title: Общие сведения о настраиваемых свойствах документа
description: Сведения о том, что при построении проекта на уровне документа Visual Studio добавляет два пользовательских свойства в документ в проекте.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 51039c71c97614cb9e43df263b3d7155c9cb86f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947805"
---
# <a name="custom-document-properties-overview"></a>Общие сведения о настраиваемых свойствах документа

При построении проекта на уровне документа Visual Studio добавляет два пользовательских свойства в документ в проекте: \_ AssemblyLocation и \_ AssemblyName. Когда пользователь открывает документ, Microsoft Office приложение проверяет наличие этих настраиваемых свойств документа. Если они существуют в документе, приложение загружает объект [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , который запускает настройку. Дополнительные сведения см. [в статье архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Это свойство содержит идентификатор CLSID интерфейса в компоненте загрузчика решений Office компонента [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Значение CLSID — 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Это значение никогда не должно изменяться.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Это свойство содержит строку, которая предоставляет сведения о манифесте развертывания для настройки. Дополнительные сведения о манифестах см. [в разделе Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 \_Значение свойства AssemblyLocation может иметь разные форматы в зависимости от способа развертывания решения:

- Если решение Опубликовано для установки с веб-сайта, пути в формате UNC или компакт-диска или устройства USB, то свойство _AssemblyLocation имеет формат *деплойментманифестпас* | *SolutionId*. Ниже приведен пример следующей строки.

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Если вы используете или выполняете отладку решения из Visual Studio, свойство _AssemblyLocation имеет формат *деплойментманифестнаме* | *SolutionId*| vstolocal. Ниже приведен пример следующей строки.

     ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionId* — это идентификатор GUID, используемый [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] для обнаружения решения. *SolutionId* создается автоматически при построении проекта. Термин **vstolocal** указывает [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , что сборка должна быть загружена из той же папки, что и документ.

## <a name="see-also"></a>См. также раздел

- [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Архитектура настроек уровня документа](../vsto/architecture-of-document-level-customizations.md)
- [Манифесты приложений и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Инструкции. Публикация решения Office с помощью ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Как создавать и изменять пользовательские свойства документа](../vsto/how-to-create-and-modify-custom-document-properties.md)