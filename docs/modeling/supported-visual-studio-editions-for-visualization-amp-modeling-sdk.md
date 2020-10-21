---
title: Поддерживаемые выпуски Visual Studio для визуализации и моделирования SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 908a224feb9f6ad463ae14812b3a8550bf932e35
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/08/2020
ms.locfileid: "92298556"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Выпуски Visual Studio, поддерживаемые пакетом SDK визуализации и моделирования

Ниже перечислены выпуски Visual Studio, которые поддерживаются [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] в средах разработки и развертывания. Дополнительные сведения об этих выпусках см. в [центре разработчиков](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Разработка версии

Для определения доменного языка необходимо установить следующие компоненты.

|Продукт|Ссылка на скачивание|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|SDK для Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Развертывание выпусков

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] поддерживает следующие конфигурации для развертывания создаваемых доменных языков:

- Visual Studio Enterprise

- Visual Studio Professional

- Оболочка Visual Studio Shell (режим интеграции), распространяемый пакет.

- Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы обеспечить возможность запуска DSL в продукте оболочки, необходимо задать поле **Supported VS Edition** в манифесте расширения. Дополнительные сведения см. в разделе [Развертывание решения на предметно-ориентированном языке](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>См. также раздел

- [Глоссарий средств предметно-ориентированных языков](/previous-versions/bb126564(v=vs.100))