---
title: "Анализ и модели архитектуры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 127
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 98d1214d1cda81102f9e03a8ce8b83886aa2c0ec
ms.openlocfilehash: 78217396085aa5531ec2cbdd5dff522201287777
ms.lasthandoff: 02/22/2017

---
# <a name="analyze-and-model-your-architecture"></a>Анализ и моделирование архитектуры
Убедитесь в том, что ваше приложение требованиям архитектуры с помощью архитектуры Visual Studio и инструментов для разработки и моделирования приложения моделирования. 

* Visual Studio поможет вам визуализировать структуру, поведение и отношения кода и разобраться в имеющемся программном коде. 

* Расскажите команды к необходимости соблюдение архитектурных зависимостей.  
  
* Программа позволяет создавать модели с разным уровнем детализации на протяжении всего жизненного цикла приложения.

В разделе [сценарий: изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).  
  
## <a name="to"></a>Кому  
  
|||  
|-|-|  
|**Визуализация кода**<br /><br /> -В разделе организацию и отношения в коде путем создания карт кода. Визуализация зависимостей между сборками, пространствами имен, классами, методами и т. д.<br />-В разделе структуры классов и членов для конкретного проекта путем создания схем классов из кода.<br />-Найти конфликты между кодом и его разработки путем создания схем зависимостей для проверки кода.|-   [Визуализация кода](../modeling/visualize-code.md)<br />-   [Работа с классами и другими типами (конструктор классов)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Видео: Понимание разработки из кода с помощью карт кода Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Видео: Проверка зависимостей архитектуры в режиме реального времени](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|  
|**Определение архитектуры**<br /><br /> — Определение и наложение ограничений на зависимости между компонентами кода путем создания схем зависимостей.|-   [Видео: Проверка архитектуры зависимостей с помощью Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Проверка системы требованиям и предназначению:**<br /><br /> -Проверка зависимостей кода с помощью схем зависимостей, которые описывают предполагаемую архитектуру и предотвращения изменений, которые могут конфликтовать с дизайном.|-   [Видео: Проверка архитектуры зависимостей с помощью Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|  
|**Совместное использование моделей, схем и карт кода с помощью системы управления версиями Team Foundation**<br /><br /> -Поместите карт кода, проектов и схем deoendency в системе управления версиями Team Foundation, чтобы сделать их.|Если в системе управления версиями Team Foundation с этими элементами работают несколько пользователей, соблюдайте приведенные здесь рекомендации. Это позволит избежать проблем с управлением версиями.<br /><br /> -   [Управление моделями и схемами в системе управления версиями](../modeling/manage-models-and-diagrams-under-version-control.md)|  
|**Настройка моделей и схем**<br /><br /> -Создайте собственные доменные языки.|-   [Пакет SDK моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
|**Создание текстов с помощью шаблонов T4**<br /><br /> -Использование блоков текста и логики управления внутри шаблона для создания текстовых файлов.<br /> -T4 шаблон сборки с MSBuild, входящих в состав Visual Studio|-   [Создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md)|

Какие версии Visual Studio поддерживают каждую функцию, в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="types-of-models-and-their-uses"></a>Типы моделей и их применение  
  
|**Тип модели и ее типичное применение**|  
|-------------------------------------|  
|**Карты кода**<br /><br /> Карты кода помогают увидеть структуру кода и имеющиеся в нем отношения.<br /><br /> Типичные способы применения:<br /><br /> -Изучите программный код, позволяет лучше понять его структуру и его зависимости, как обновить и оценить затраты на предлагаемых изменений.<br /><br /> См. следующие разделы:<br /><br /> -   [Сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Поиск потенциальных проблем, с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)|  
|**Диаграмма зависимостей**<br /><br /> Диаграммы зависимостей позволяют определить структуру приложения как набор слоев или блоков с явными зависимостями. Можно выполнить проверку, чтобы обнаруживать конфликты между зависимостями в коде и зависимостями, описанными в схеме зависимостей.<br /><br /> Типичные способы применения:<br /><br /> -Стабилизация структуры приложения при многочисленных изменениях в течение его жизненного цикла.<br />-Выявление непредвиденных конфликтов зависимостей перед возвратом изменений кода.<br /><br /> См. следующие разделы:<br /><br /> -   [Создание схем зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Схемы зависимостей: Справочник](../modeling/layer-diagrams-reference.md)<br />-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|  
|**Доменный язык (DSL)**<br /><br /> Предметно-ориентированный язык представляет собой нотацию, разработанную для определенной цели. В Visual Studio обычно используется графическая нотация.<br /><br /> Типичные способы применения:<br /><br /> -Создание или настройка частей приложения. Разработка нотации и инструментов требует усилий. Результат может лучше соответствовать вашему домену, чем настройка языка UML.<br />-Для больших проектов или линеек продуктов, где затраты на разработку DSL и его средства возвращается путем использования в нескольких проектах.<br /><br /> См. следующие разделы:<br /><br /> -   [Пакет SDK моделирования для Visual Studio — доменные языки](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|  
  
## <a name="where-can-i-get-more-information"></a>Где можно получить дополнительные сведения?  
  
[Visual Studio визуализации & форум, посвященный средствам моделирования](http://go.microsoft.com/fwlink/?LinkId=184720)  
  
## <a name="see-also"></a>См. также  
 [Новые возможности](../modeling/what-s-new-for-design-in-visual-studio.md)   
 [Разработка и управление жизненным циклом приложений](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)

