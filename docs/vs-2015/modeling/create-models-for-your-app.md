---
title: Создание моделей для приложения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: feb0c1a5f486654844c592b6b946dedc9e2e02c0
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2019
ms.locfileid: "59002195"
---
# <a name="create-models-for-your-app"></a>Создание моделей для приложения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Схемы моделирования помогают понять, уточнить и передать другим сведения о коде и пользовательских требованиях, которым должна удовлетворять ваша программная система. Например, для описания и передачи пользовательских требований можно использовать схемы UML вариантов использования, деятельности, классов и последовательностей. Для описания функциональных возможностей системы и передачи сведений о них можно использовать схемы UML компонентов, классов, деятельности и последовательностей.  
  
 См. в разделе [видео на Channel 9: Совершенствование архитектуры путем моделирования](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 В этом выпуске можно создавать следующие UML-схемы:  
  
|**Схема**|**Что показывает**|  
|-----------------|---------------|  
|[Схемы активности UML: справочник](../modeling/uml-activity-diagrams-reference.md)|Поток работы между действиями и участниками в рамках бизнес-процесса|  
|[Схемы компонентов UML: справочник](../modeling/uml-component-diagrams-reference.md)|Компоненты системы, их интерфейсы, порты и отношения|  
|[Схемы классов UML: справочник](../modeling/uml-class-diagrams-reference.md)|Типы, используемые для хранения данных  и их отношений и обмена ими в системе|  
|[Схемы последовательностей UML: справочник](../modeling/uml-sequence-diagrams-reference.md)|Последовательности взаимодействий между объектами, компонентами, системами или субъектами|  
|[Схемы вариантов использования UML: справочник](../modeling/uml-use-case-diagrams-reference.md)|Цели и задачи пользователей, поддерживаемые системой|  
  
 Чтобы узнать, какие версии Visual Studio поддерживают разные типы схем, см. в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Для визуализации архитектуры системы или имеющегося кода создайте следующие схемы:  
  
|**Схема**|**Что показывает**|  
|-----------------|---------------|  
|[Схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Схемы слоев: справочник](../modeling/layer-diagrams-reference.md)|Высокоуровневая архитектура системы|  
|Карты кода<br /><br /> [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)|Зависимости и другие отношения в имеющемся коде|  
|Схемы классов, созданные кодом<br /><br /> [Работа со схемами классов (конструктор классов)](../ide/working-with-class-diagrams-class-designer.md)|Типы и их отношения в коде .NET|  
  
## <a name="common-tasks"></a>Общие задачи  
  
|**Раздел**|**Задача**|  
|---------------|--------------|  
|[Создание проектов и схем моделирования UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Создание моделей** и добавляйте схемы.|  
|[Изменение моделей и схем UML](../modeling/edit-uml-models-and-diagrams.md)|**Нарисуйте схемы** для редактирования модели.|  
|[Определение пакетов и пространств имен](../modeling/define-packages-and-namespaces.md)|**Создание пакетов** Чтобы разделить модель на единицы, которыми могут работать разные члены команды.|  
|[Создание кода на основе схем классов UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Создание кода C# из схем классов** для запуска своей реализации.|  
|[Настройка модели с помощью профилей и стереотипов](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Настраивайте элементы модели** с использованием стереотипов, чтобы расширить стандартные элементы модели UML для выполнения конкретных задач.|  
|[Связывание элементов модели и рабочих элементов](../modeling/link-model-elements-and-work-items.md)|**Создавать ссылки между элементами модели и рабочими элементами** помогут отслеживать задачи, тестовые случаи, ошибки, требования, проблемы и другие виды работ, которые связаны с определенными частями модели.|  
|[Экспорт схем в виде изображений](../modeling/export-diagrams-as-images.md)|**Сохраните модель и схемы** таким образом, чтобы использовать их совместно с другими пользователями, включая тех, кто не используйте [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|**Раздел**|**Задача**|  
|---------------|--------------|  
|[Визуализация кода](../modeling/visualize-code.md)|Создавайте карты кода и схемы слоев, чтобы лучше разобраться в незнакомом коде.|  
|[Моделирование требований пользователей](../modeling/model-user-requirements.md)|Используйте модели для уточнения потребностей пользователей и передачи информации о них.|  
|[Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)|Используйте модели, чтобы описать общую структуру и поведение системы, а также обеспечить ее соответствие потребностям пользователей.|  
|[Проверка системы в ходе разработки](../modeling/validate-your-system-during-development.md)|Убедитесь, что программное обеспечение соответствует потребностям пользователей и общей архитектуре системы.|  
|[Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)<br /><br /> [Использование моделей в гибкой разработке](http://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Используйте модели, чтобы изучить и изменить систему во время разработки.|  
|[Разработка структуры решения моделирования](../modeling/structure-your-modeling-solution.md)|Упорядочивайте модели в рамках проекта большого или среднего размера.|  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
|**Категория**|**Links**|  
|------------------|---------------|  
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
