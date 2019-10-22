---
title: Справочник по API для расширяемости моделирования UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672807"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Справочник по API для расширения моделей UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете написать программный код для чтения и изменения моделей, созданных с помощью Visual Studio. Справочник по API содержит информацию об определенных классах, помогающих справиться с этой задачей. Дополнительные сведения о задачах см. в разделах, посвященных [расширению моделей UML и схем](../modeling/extend-uml-models-and-diagrams.md). Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Сборки

|Assembly|Возможности|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|— Чтение и изменение элементов модели, таких как Иусекасе, ИассоЦиатион и т. д.<br />— Навигация по связям между элементами.<br /><br /> Пространства имен и типы соответствуют пространствам имен и типам, которые определены в спецификации UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|— Создание новых экземпляров элементов модели<br />— Доступ и изменение фигур и схем.|

## <a name="see-also"></a>См. также раздел
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md) [Справочник по API для моделирования пакета SDK для Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
