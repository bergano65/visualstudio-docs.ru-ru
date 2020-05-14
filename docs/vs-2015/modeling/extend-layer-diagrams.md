---
title: Расширяйте диаграммы слоя Документы Майкрософт
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301257"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете написать код для создания и обновления схем слоев и для проверки структуры кода программы по схемам слоев в Visual Studio. Вы можете добавить команды, которые отображаются в контекстном меню схем, настроить жесты перетаскивания, а также получить доступ к модели слоев из текстовых шаблонов. Вы можете упаковать эти расширения в расширение Visual Studio Integration Extension (VSIX) и предоставить их другим пользователям Visual Studio.

 Более подробную информацию о схемах слоев см. в следующих разделах:

- [Схемы слоев: справочные материалы](../modeling/layer-diagrams-reference.md)

- [Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)

- [Создание схем слоев на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

- [Проверка кода по схемам слоев](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a>Требования
 На компьютере, где планируется разрабатывать расширения слоев, должны быть установлены следующие компоненты:

- Visual Studio

- [Пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md)

- [Моделирование SDK для визуальной студии 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  На компьютере, где планируется выполнять расширения слоев, должна быть установлена подходящая версия Visual Studio. Для получения дополнительной информации [см. Развертывание расширения модели слоя.](../modeling/deploy-a-layer-model-extension.md)

  Чтобы узнать, какие версии Visual Studio поддерживают схемы слоев, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>в этом разделе
 [Добавление команд и жестов в схемы слоев](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Добавление пользовательской проверки архитектуры в схемы слоев](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Добавление пользовательских свойств в схемы слоев](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Перемещение по моделям слоев в коде программы и их обновление](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Развертывание расширения модели слоев](../modeling/deploy-a-layer-model-extension.md)

 [Устранение неполадок, связанных с расширениями для схем слоев](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>См. также:
 [Определите и установите](../modeling/define-and-install-a-modeling-extension.md) диаграммы слоя расширения [моделирования: Диаграммы референтного](../modeling/layer-diagrams-reference.md) [слоя: Руководящие принципы](../modeling/layer-diagrams-guidelines.md) [Создание диаграмм слоя из](../modeling/create-layer-diagrams-from-your-code.md) кода Validate с [помощью диаграмм слоя](../modeling/validate-code-with-layer-diagrams.md) [Генерируйте файлы из модели UML](../modeling/generate-files-from-a-uml-model.md) [Откройте модель UML с помощью Visual Studio API](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
