---
title: Extend layer diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301034"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете написать код для создания и обновления схем слоев и для проверки структуры кода программы по схемам слоев в Visual Studio. Вы можете добавить команды, которые отображаются в контекстном меню схем, настроить жесты перетаскивания, а также получить доступ к модели слоев из текстовых шаблонов. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

 Более подробную информацию о схемах слоев см. в следующих разделах:

- [Схемы слоев: справочные материалы](../modeling/layer-diagrams-reference.md)

- [Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)

- [Создание схем слоев на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

- [Проверка кода по схемам слоев](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> Требования
 На компьютере, где планируется разрабатывать расширения слоев, должны быть установлены следующие компоненты:

- Visual Studio

- [SDK для Visual Studio](../extensibility/visual-studio-sdk.md)

- [Modeling SDK for Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  На компьютере, где планируется выполнять расширения слоев, должна быть установлена подходящая версия Visual Studio. For more information, see [Deploy a layer model extension](../modeling/deploy-a-layer-model-extension.md).

  Чтобы узнать, какие версии Visual Studio поддерживают схемы слоев, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Содержание
 [Добавление команд и жестов в схемы слоев](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Добавление пользовательских свойств в схемы слоев](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Перемещение по моделям слоев в коде программы и их обновление](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Развертывание расширения модели слоев](../modeling/deploy-a-layer-model-extension.md)

 [Устранение неполадок, связанных с расширениями для схем слоев](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>См. также раздел
 [Define and install a modeling extension](../modeling/define-and-install-a-modeling-extension.md) [Layer Diagrams: Reference](../modeling/layer-diagrams-reference.md) [Layer Diagrams: Guidelines](../modeling/layer-diagrams-guidelines.md) [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md) [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md) [Generate files from a UML model](../modeling/generate-files-from-a-uml-model.md) [Open a UML model by using the Visual Studio API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
