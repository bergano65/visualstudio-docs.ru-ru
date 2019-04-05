---
title: Программирование с UML API | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24f4f21c984f70ca10236de7bf15d0187fd12d71
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979460"
---
# <a name="programming-with-the-uml-api"></a>Programming with the UML API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML API Visual Studio позволяет написать код для создания, чтения и обновления моделей и схем UML. Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 API описывается на страницах справочных материалов об API и в следующих разделах.  
  
|Раздел|Примеры описываемых типов и методов|Описываемые функции|  
|-----------|-----------------------------------------|------------------------|  
|[Переход по отношениям с помощью UML API](../modeling/navigate-relationships-with-the-uml-api.md)|UML-элементы, их свойства и ассоциации. Например IElement и его потомки, включая: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel и IPackage|В Visual Studio модели UML соответствуют версии 2.1.2 спецификации UML, который можно получить в [странице ресурсов UML](http://go.microsoft.com/fwlink/?LinkId=160796). Каждый тип является интерфейсом, имя которого совпадает с именем типа UML с префиксом "I".|  
|[Создание элементов и отношений в моделях UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Каждый тип элемента имеет методы для создания дочерних элементов.|  
|[Отображение модели UML на схемах](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Каждый элемент в модели может быть представлен в виде фигуры на схеме. В некоторых случаях можно создавать новые фигуры для каждого объекта. Эти фигуры можно перемещать, сворачивать или разворачивать, а также изменять их размер и цвет.|  
|[Навигация по модели UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Модель хранится в хранилище моделей.<br /><br /> Контекст схемы предоставляет доступ к текущей схеме и хранилищу.|  
|[Связывание обновлений модели UML с использованием транзакций](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Ряд изменений можно связать в одну транзакцию.|  
|[Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Чтобы расширить функциональные возможности схемы, нужно определить команды, вызываемые двойным щелчком мыши, и перетащить их на схему.|  
|[Определение ограничений проверки для моделей UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Для контроля соответствия модели определенным ограничениям можно настроить правила проверки.|  
|[Получение элементов модели UML из IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Если элемент перетаскивается из обозревателя моделей UML или схемы UML на другую схему или в другое приложение, он сериализуется как IDataObject.|  
|[Редактирование схем последовательностей UML с помощью API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Создание и обновление схемы взаимодействия несколько отличается от работы с другими типами схем.|  
|[Расширение схем слоев](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Можно написать код для создания и редактирования схем слоев, а также для проверки кода программы на соответствие схемам слоев.|  
  
## <a name="about-the-implementation"></a>О реализации  
 В основе средств моделирования UML лежат [!INCLUDE[dsl](../includes/dsl-md.md)]. Каждый пакет и каждая схема представлены моделью [!INCLUDE[dsl](../includes/dsl-md.md)], а соответствие между ними обеспечивается коллекцией правил и другими методами.  
  
 Типы из этой платформы видны в некоторых сборках, на которые дается ссылка при создании UML-расширений. Несмотря на то что расширения для инструментов UML можно создавать, обращаясь к API [!INCLUDE[dsl](../includes/dsl-md.md)], необходимо помнить о следующем.  
  
-   Может оказаться, что некоторые кажущиеся простыми изменения вызывают несоответствия и дают непредвиденные результаты.  
  
-   В будущем реализация может измениться, и изменения, внесенные с помощью API [!INCLUDE[dsl](../includes/dsl-md.md)] окажутся недействительными.  
  
## <a name="the-api-assemblies"></a>Сборки API  
 В этой таблице представлены сборки, позволяющие расширять инструменты UML, и пространства имен, которые рекомендуется использовать.  
  
|Assembly|Пространства имен|К чему предоставляет доступ|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(Все)|Типы UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[Методы создания](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[Схемы и фигуры](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[Проект моделирования](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[версия]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Расширение команды меню](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Связанные транзакции отмены](../modeling/link-uml-model-updates-by-using-transactions.md).|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Проверка](../modeling/define-validation-constraints-for-uml-models.md)|  
||(другие пространства имен)|Рекомендуется только для опытных пользователей.|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[версия]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Обработчики жестов](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|  
||(другие пространства имен)|Рекомендуется только для опытных пользователей.|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[Ссылки на рабочие элементы](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[Рабочие элементы и их поля](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[Рабочие элементы и их поля](../modeling/define-a-work-item-link-handler.md).|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Экспорт и импорт компонентов MEF](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[Простое управление коллекциями, особенно при работе со связями](../modeling/navigate-relationships-with-the-uml-api.md).|  
  
## <a name="see-also"></a>См. также  
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Справочник по API для расширения моделей UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
