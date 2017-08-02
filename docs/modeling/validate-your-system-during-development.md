---
title: "Проверка системы во время разработки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 37
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
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: d35e357a62c467d20f5a97a469ac5f89324b4391
ms.lasthandoff: 02/22/2017

---
# <a name="validate-your-system-during-development"></a>Проверка системы в ходе разработки
Visual Studio помогает привести в соответствие программное обеспечение, требования пользователей и архитектуру системы.  
  
 Чтобы узнать, какие версии Visual Studio поддерживают каждый из этих компонентов, см. раздел [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Ключевые задачи  
 Для проверки программного обеспечения используйте приведенные ниже задачи.  
  
|**Задачи**|**Связанные разделы**|  
|---------------|---------------------------|  
|**Убедитесь, что программное обеспечение соответствует требованиям пользователей**:<br /><br /> Чтобы организовать тесты системы и компонентов, можно использовать требования и модели архитектуры. Такой подход позволяет обеспечить проверку требований, важных для пользователей и других заинтересованных лиц, и помогает быстро обновлять тесты при изменении требований.|-   [Разработка тестов из модели](../modeling/develop-tests-from-a-model.md)|  
|**Убедитесь, что программное обеспечение соответствует предполагаемой структуре системы:**<br /><br /> Схемы зависимостей описывают предполагаемые зависимости между компонентами приложения. В процессе разработки можно следить за тем, чтобы фактические зависимости в коде соответствовали предполагаемой структуре.|-   [Создание схем зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
|**Категории**|**Ссылки**|  
|------------------|---------------|  
|**Видео**|![ссылка на видео](~/data-tools/media/playvideo.gif "PlayVideo") [Channel 9: семь дуг: понимание кода и разработка систем в Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![ссылка на видео](~/data-tools/media/playvideo.gif "PlayVideo") [Channel 9: разработка архитектуры приложения с помощью схемы зависимостей](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![ссылка на видео](~/data-tools/media/playvideo.gif "PlayVideo") [MSDN как серия: проверка кода с помощью схем зависимостей](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Форумы**|-   [Visual Studio визуализации & средства моделирования](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio визуализации & моделирования SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Блоги**|-   [Visual Studio ALM + блог Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Технические статьи и журналы**|[Центр MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>См. также  
 [Тестирование приложения](https://www.visualstudio.com/en-gb/docs/test/overview)   
 [Моделирование требований пользователей](../modeling/model-user-requirements.md)   
 [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

