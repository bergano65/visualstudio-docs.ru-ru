---
title: "Визуализация кода | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 47
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: aa7e0e7e9bbd4d4a3f8a1b2fa82f1ce7a6ba3e53
ms.lasthandoff: 02/22/2017

---
# <a name="visualize-code"></a>Визуализация кода
Вы можете использовать средства визуализации и моделирования в Visual Studio, чтобы анализировать существующий код и описать приложение. Это позволяет наглядно изучить, как изменения могут повлиять на код, а также оценить работы и риски, возникающие в результате этих изменений. Например:  
  
-   Чтобы понять связи в коде, сопоставьте их визуально.  
  
-   Для описания архитектуры системы и обеспечить соответствие кода его дизайну, создайте схемы зависимостей и проверить код на соответствие этим схемам.  
  
-   Для описания структур классов создайте схемы классов.  
  
 Кроме того, эти средства облегчают взаимодействие с другими участниками проекта. 
  
 Какие версии Visual Studio поддерживают каждую функцию, в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>Выберите действие  
  
|||  
|-|-|  
|**Понимание кода и его связей.**<br /><br /> Установите связи между определенными частями кода.<br /><br /> Получите общие сведения о связях в коде для всего решения.<br /><br /> **Примечание**. В этой версии Visual Studio термин *карта кода* используется вместо *графа зависимостей*.|-   [Сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Поиск потенциальных проблем, с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Сопоставление методов в стеке вызовов при отладке](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Анализ структуры классов:**<br /><br /> Визуализируйте структуру классов в проекте путем создания схем классов на основе кода.|[Практическое руководство. Добавление схем классов в проекты (конструктор классов)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Описывается высокоуровневую структуру системы и проверить код на соответствие этой структуре.**<br /><br /> Описаны высокоуровневую структуру системы и ее предполагаемые зависимости путем создания схем зависимостей. Проверьте код на соответствие этой структуре, чтобы убедиться в том, что зависимости в коде согласованы с ней.|-   [Создание схем зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Схемы зависимостей: Справочник](../modeling/layer-diagrams-reference.md)<br />-   [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)<br />-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
|**Категории**|**Ссылки**|  
|------------------|---------------|  
|**Форумы**|-   [Visual Studio визуализации & средства моделирования](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio визуализации & моделирования SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Блоги**|[Visual Studio ALM + блог Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Технические статьи и журналы**|[Форум MSDN по архитектуре](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>См. также  
 [Сценарий: Изменение проекта с помощью визуализации и моделирования](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [Анализ и моделирование архитектуры](../modeling/analyze-and-model-your-architecture.md)   
 [Моделирование архитектуры приложения](../modeling/model-your-app-s-architecture.md)   
 [Использование моделей в процессе разработки](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

