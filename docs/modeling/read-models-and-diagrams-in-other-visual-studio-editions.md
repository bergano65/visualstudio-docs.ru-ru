---
title: "Чтение моделей и схем в других выпусках Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 20
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
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 9ffc4c39dee2da1d6daa051f478eac18d9670151
ms.lasthandoff: 02/22/2017

---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Чтение моделей и схем в других выпусках Visual Studio
При открытии модели в версии Visual Studio, которая не поддерживает создание моделей, она открывается в режиме "только для чтения". В этом режиме можно изменить структуру схемы, но невозможно изменить модель.  
  
 Какие версии Visual Studio поддерживают создание моделей см. [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Получение доступа к модели и схемам  
 Чтобы прочитать схему зависимостей, необходимо сначала с помощью Visual Studio откройте проект моделирования и затем открыть схему в этом.  
  
 По этой причине если вы хотите прочитать схему зависимостей, необходимо также иметь доступ в проект моделирования, в котором он был создан. Для этого нужно либо открыть проект из [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)], либо получить копию файлов проекта.  
  
> [!NOTE]
>  Это не относится к картам кода и схемам классов .NET, созданным из кода. Эти схемы можно просматривать независимо от проекта моделирования.  
  
 Чтобы прочитать схему зависимостей, минимальный набор необходимых файлов выглядит следующим образом:  
  
-   Два файла схемы для схемы, который требуется прочитать, например, **MyDiagram.classdiagram и MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Диаграммы зависимостей должны иметь файл с именем *Моя_схема***. layerdiagram.suppressions**.  
  
-   Файл проекта моделирования (**MyModel.modelproj**)  
  
-   Файл корневой модели (**ModelDefinition\MyModel.uml**)  
  
-   Файлы пакета для любого пакета, на который ссылается на диаграмме (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Изменения, которые можно внести в режиме только для чтения  
 Если открыть модель и ее схемы в версии Visual Studio, которая не поддерживает создание модели, то модель нельзя будет изменять. То есть нельзя изменять элементы и отношения, которые отображаются на схемах или в обозревателе моделей. Однако можно внести некоторые изменения в структуру схем:  
  
-   изменить расположение фигур и соединителей на схеме;  
  
-   развернуть или свернуть фигуры.  
  
 Эти изменения можно сохранить. Если вы хотите сделать изменения видимыми для других пользователей, необходимо хотя бы отправить обновленные **.layout** файлов.  
  
##  <a name="a-namerelatedtopicsa-related-topics"></a><a name="RelatedTopics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Схемы зависимостей: Справочник](../modeling/layer-diagrams-reference.md)|На схеме слоев показана структура существующей или предложенной архитектуры. При создании кода его можно автоматически проверить относительно схемы слоев.|  
  
## <a name="see-also"></a>См. также  
 [Создание моделей для приложения](../modeling/create-models-for-your-app.md)
