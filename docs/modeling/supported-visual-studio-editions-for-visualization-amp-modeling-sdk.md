---
title: Поддерживаемые выпуски Visual Studio для визуализации и моделирования SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 65014d8c697adbf5fb8e13d28708090360bb9c17
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049960"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Выпуски Visual Studio, поддерживаемые пакетом SDK визуализации и моделирования

Ниже приведены списки, которые поддерживаются в выпусках Visual Studio [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] в средах разработки и развертывания. Дополнительные сведения об этих выпусках см. в разделе Microsoft Visual Studio [Центр разработчиков](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Разработка версии

Для определения доменного языка необходимо установить следующие компоненты.

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK для Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Пакет SDK для визуализации и моделирования в Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Развертывание выпусков

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] поддерживает следующие конфигурации для развертывания доменных языков, которые вы создаете:

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Распространяемый пакет распространяемого пакета Visual Studio Shell (интегрированный режим)

-   Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы доменный язык может работать на продукте оболочки, необходимо задать **поддерживаемая версия VS** в манифесте расширения. Дополнительные сведения см. в разделе [развертывание решений предметно-ориентированного языка](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>См. также

- [Глоссарий по средствам доменного языка работы](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)