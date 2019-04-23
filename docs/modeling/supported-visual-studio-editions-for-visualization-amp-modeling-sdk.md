---
title: Поддерживаемые выпуски Visual Studio для визуализации и моделирования SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e5898a95f10875f0880e4b4799f17b78aa8e79b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073336"
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

- Visual Studio Enterprise

- Visual Studio Professional

- Распространяемый пакет распространяемого пакета Visual Studio Shell (интегрированный режим)

- Оболочка Visual Studio Shell (изолированный режим), распространяемый пакет.

> [!NOTE]
> Чтобы доменный язык может работать на продукте оболочки, необходимо задать **поддерживаемая версия VS** в манифесте расширения. Дополнительные сведения см. в разделе [развертывание решений предметно-ориентированного языка](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>См. также

- [Глоссарий по средствам доменного языка работы](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)