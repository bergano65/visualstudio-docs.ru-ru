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
ms.openlocfilehash: b81aaba14acc2c050a770e810c57e99ee43c2ab3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298154"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Поддерживаемые выпуски Visual Studio для визуализации SDK &amp; моделирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ниже перечислены выпуски Visual Studio, которые поддерживаются [!INCLUDE[dsl](../includes/dsl-md.md)] в средах разработки и развертывания. Дополнительные сведения об этих выпусках см. в [центре разработчиков](https://go.microsoft.com/fwlink/?LinkId=75628)[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Майкрософт.

## <a name="authoring-edition"></a>Разработка версии
 Для определения доменного языка необходимо установить следующие компоненты.

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK для Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

## <a name="deployment-editions"></a>Развертывание выпусков
 [!INCLUDE[dsl](../includes/dsl-md.md)] поддерживает следующие конфигурации для развертывания создаваемых доменных языков.

- Visual Studio Enterprise

- Visual Studio Professional

- Распространяемый пакет распространяемого пакета Visual Studio Shell (интегрированный режим)

- Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы обеспечить возможность запуска DSL в продукте оболочки, необходимо задать поле **Supported VS Edition** в манифесте расширения. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>См. также
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
