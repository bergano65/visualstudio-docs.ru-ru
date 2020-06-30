---
title: Поддерживаемые выпуски Visual Studio для визуализации и моделирования SDK | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547658"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Поддерживаемые выпуски Visual Studio для &amp; пакета SDK для моделирования визуализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ниже перечислены выпуски Visual Studio, которые поддерживаются [!INCLUDE[dsl](../includes/dsl-md.md)] в средах разработки и развертывания. Дополнительные сведения об этих выпусках см. в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [центре разработчиков](https://msdn.microsoft.com/vstudio/products/)Майкрософт.

## <a name="authoring-edition"></a>Разработка версии
 Для определения доменного языка необходимо установить следующие компоненты.

|Продукт|Ссылка на скачивание|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[SDK для Visual Studio](../extensibility/visual-studio-sdk.md)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[Загрузка пакета SDK для моделирования](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Развертывание выпусков
 [!INCLUDE[dsl](../includes/dsl-md.md)]поддерживает следующие конфигурации для развертывания создаваемых доменных языков:

- Visual Studio Enterprise

- Visual Studio Professional

- Оболочка Visual Studio Shell (режим интеграции), распространяемый пакет.

- Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы обеспечить возможность запуска DSL в продукте оболочки, необходимо задать поле **Supported VS Edition** в манифесте расширения. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>См. также
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
