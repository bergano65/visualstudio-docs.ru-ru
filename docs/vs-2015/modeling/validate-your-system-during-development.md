---
title: Проверка системы во время разработки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8b0d65d99cf99c7f1468a0bf596eb687f931b5d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570855"
---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [проверка системы во время разработки](https://docs.microsoft.com/visualstudio/modeling/validate-your-system-during-development).  
  
Visual Studio помогает привести в соответствие программное обеспечение, требования пользователей и архитектуру системы.  
  
 Чтобы узнать, какие версии Visual Studio поддерживают каждую функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Ключевые задачи  
 Для проверки программного обеспечения используйте приведенные ниже задачи.  
  
|**Задачи**|**Связанные разделы**|  
|---------------|---------------------------|  
|**Убедитесь, что ваша модель становится согласованные:**<br /><br /> В зависимости от способа использования и интерпретации моделей в проекте может оказаться полезным запретить некоторые сочетания элементов. Например, в качестве ограничения для классов UML можно потребовать их обязательной совместимости с [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]. Подобные ограничения можно определять в расширениях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|-   [Проверка модели UML](../modeling/validate-your-uml-model.md)<br />-   [Определение ограничений проверки для моделей UML](../modeling/define-validation-constraints-for-uml-models.md)|  
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br /> Чтобы организовать тесты системы и компонентов, можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|-   [Разработка тестов из модели](../modeling/develop-tests-from-a-model.md)|  
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br /> Схемы слоев описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|-   [Создание схем слоев из кода](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Проверка кода по схемам слоев](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
|**Категория**|**Ссылки**|  
|------------------|---------------|  
|**Видеоролики**|![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: семь дуг: понимание кода и разработка систем в Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: разработка архитектуры приложения с помощью схемы слоев](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") [MSDN практические руководства: проверка кода с использованием схем слоев](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Форумы**|-   [Средства моделирования и визуализации Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Пакет SDK для моделирования и визуализации в Visual Studio (инструменты DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Блоги**|-   [Блог по Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Технические статьи и журналы**|[Центр архитекторов на MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>См. также  
 [Тестирование приложения](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Моделирование требований пользователей](../modeling/model-user-requirements.md)   
 [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)



