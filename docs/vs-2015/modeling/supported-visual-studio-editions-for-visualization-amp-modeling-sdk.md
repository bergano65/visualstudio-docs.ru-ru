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
ms.openlocfilehash: 227c2871f68545c9f9fe5fa1ea3ceee827ccdc6a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917308"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Поддерживаемые выпуски Visual Studio для визуализации SDK &amp; моделирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ниже приведены списки, которые поддерживаются в выпусках Visual Studio [!INCLUDE[dsl](../includes/dsl-md.md)] в средах разработки и развертывания. Дополнительные сведения об этих выпусках см. в [центре разработчиков](https://msdn.microsoft.com/vstudio/products/)[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Майкрософт.

## <a name="authoring-edition"></a>Разработка версии
 Для определения доменного языка необходимо установить следующие компоненты.

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[Загрузка пакета SDK для моделирования](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Развертывание выпусков
 [!INCLUDE[dsl](../includes/dsl-md.md)] поддерживает следующие конфигурации для развертывания доменных языков, которые вы создаете:

- Visual Studio Enterprise

- Visual Studio Professional

- Распространяемый пакет распространяемого пакета Visual Studio Shell (интегрированный режим)

- Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы доменный язык может работать на продукте оболочки, необходимо задать **поддерживаемая версия VS** в манифесте расширения. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>См. также раздел
 [Глоссарий средств предметно-ориентированных языков](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
