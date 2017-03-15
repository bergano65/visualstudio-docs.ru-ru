---
title: "Правила распространяют изменения в пределах модели | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Доменный язык, программирование доменных моделей"
  - "Доменный язык, правила"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 30
---
# Правила распространяют изменения в пределах модели
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создать правило хранилища для распространения изменений из одного элемента в другой в визуализации и моделирования SDK \(VMSDK\). При изменении любого элемента в хранилище правил запланированы для выполнения, обычно при фиксации внешней транзакции. Существуют различные типы правил для различных типов событий, таких как добавление элемента или удалить его. Правила можно присоединить к определенным типам элементов, фигуры или схемы. Многие встроенные функции определяются правилами: например, правила гарантируют, что схема обновляется при изменении модели. Доменный язык можно настроить, добавив собственные правила.  
  
 Сохранить правила особенно полезны, внесение изменений в хранилище — то есть, изменений в элементы модели, отношения, фигуры или соединители и их домена свойства. Правила не выполняются при вызове пользователем команды отмены или повтора. Вместо этого диспетчер транзакций гарантирует, что содержимое хранилища восстанавливаются в правильном состоянии. Если вы хотите распространить изменения к ресурсам за пределами хранилища, используйте хранения событий. Дополнительные сведения см. в разделе [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Например предположим, что требуется указать, что всякий раз, когда пользователь \(или код\) создает новый элемент типа ExampleDomainClass, дополнительный элемент другого типа создается в другой части модели. Можно написать методы AddRule и связать его с ExampleDomainClass. Можно написать код, в правиле для создания дополнительных элементов.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  Код правила следует изменить состояние только элементы в хранилище; то есть правило следует изменить только элементы модели, отношения, фигуры, соединители, схем или их свойства. Если вы хотите распространить изменения к ресурсам за пределами хранилища, определите хранения событий. Дополнительные сведения см. в разделе [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
### Определение правила  
  
1.  Определите правило, как класс с префиксом `RuleOn` атрибута. Этот атрибут связывает правило с помощью одного из классов доменов, связи или элементов диаграммы. Правило будет применяться к каждому экземпляру этого класса, который может быть абстрактным.  
  
2.  Зарегистрировать правило, добавьте его в набор, возвращаемый `GetCustomDomainModelTypes()` в классе модели домена.  
  
3.  Является производным класса правила от абстрактных классов правило и написать код метода выполнения.  
  
 В следующих разделах описаны эти этапы в деталях.  
  
### Чтобы определить правила для класса домена  
  
-   В файле пользовательский код определения класса и перед ними <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> атрибута:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Тип субъекта, в качестве первого параметра может быть класс домена, отношения между доменом, фигуры, соединителя или схемы. Как правило применяются правила для классов доменов и отношений.  
  
     `FireTime` Обычно `TopLevelCommit`. Это гарантирует, что правило выполняется только после внесения всех основные изменения транзакции. Альтернативами являются встроенными, который выполняет правила вскоре после изменения; и LocalCommit, в котором выполняется правило в конце текущей транзакции \(что может оказаться самым внешним\). Можно также задать приоритет правила влияет на порядок в очереди, но это ненадежный метод достижения результата, который требуется.  
  
-   Абстрактный класс можно указать тип субъекта.  
  
-   Правило применяется ко всем экземплярам класса субъекта.  
  
-   Значение по умолчанию `FireTime` — TimeToFire.TopLevelCommit. В результате правило для выполнения при фиксации внешней транзакции. Альтернативой является TimeToFire.Inline. В результате правило должно выполняться сразу после запускающее событие.  
  
### Чтобы зарегистрировать правило  
  
-   Добавить правило в список типов, возвращаемых `GetCustomDomainModelTypes` в модели домена:  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Если вы не уверены в правильности имени класс модели домена, найдите в файле **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   Этот код записывается в файл пользовательского кода в проекте DSL.  
  
### Чтобы написать код правила  
  
-   Создайте правило класс, производный от одного из следующих базовых классов:  
  
    |Базовый класс|Триггер|  
    |-------------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Добавлен элемент, ссылку или фигуры.<br /><br /> Позволяет обнаруживать новые связи, а также новые элементы.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|При изменении значения свойства домена. Аргумент метода содержит старые и новые значения.<br /><br /> Для фигур, это правило срабатывает при встроенной `AbsoluteBounds` изменения свойств, при перемещении фигуры.<br /><br /> Во многих случаях это более удобным для переопределения `OnValueChanged` или `OnValueChanging` в обработчике свойств. Эти методы вызываются непосредственно перед и после изменения. В отличие от этого правила обычно выполняется в конце транзакции. Для получения дополнительной информации см. [Обработчики изменений значений свойств доменов](../modeling/domain-property-value-change-handlers.md). **Note:**  Это правило не выполняется, когда создается или удаляется ссылка. Вместо этого записывать `AddRule` и `DeleteRule` для связи домена.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Запускается, когда элемент или ссылку для удаления. Свойство ModelElement.IsDeleting имеет значение true до конца транзакции.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Выполняется при удалении элемента или связи. Правила выполняются после выполнены все правила, включая DeletingRules. ModelElement.IsDeleting значение false, а ModelElement.IsDeleted имеет значение true. Чтобы разрешить для последующих отката, элемент не удаляется из памяти, но он удаляется из Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Элемент перемещается из одного хранилища секции в другую.<br /><br /> \(Обратите внимание, что это не связано с графического положения фигуры\).|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Это правило применяется только к доменных связей. Он срабатывает, если на обоих концах канала явным образом присвоить элементу модели.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Запускается при порядок ссылок в или из элемента изменяется с помощью методов MoveBefore или MoveToIndex связи.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Выполняется при создании транзакции.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Выполняется при фиксации транзакции.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Выполняется, когда откат транзакции.|  
  
-   Каждый класс имеет метод, который можно переопределить. Тип `override` в классе для его обнаружения. Параметр этого метода определяет элемент, который изменяется.  
  
 Обратите внимание на следующие моменты, о правилах:  
  
1.  Набор изменений в транзакции может вызвать много правил. Как правило правила выполняются при фиксации внешней транзакции. Они выполняются в неопределенном порядке.  
  
2.  Правило всегда выполняется в транзакции. Поэтому не требуется создавать новую транзакцию для внесения изменений.  
  
3.  Правила не выполняются при откате транзакции, или при выполнении операций отмены или повтора. Эти операции Сброс всего содержимого хранилища в предыдущее состояние. Таким образом Если правило изменяет состояние ничего за пределы хранилища, он может не хранятся в synchronism с хранилищем содержимого. Чтобы обновить состояние за пределы хранилища, лучше использовать события. Дополнительные сведения см. в разделе [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Некоторые правила выполняются, когда модель загружается из файла. Чтобы определить, является ли ход выполнения загрузки или сохранения, используйте `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Если код правила создает дополнительные правила триггеров, они будут добавлены в конец списка срабатывание и будет выполнен до завершения транзакции. DeletedRules выполняются после всех остальных. Одно правило можно запускать множество раз в транзакции, один раз для каждого изменения.  
  
6.  Для передачи информации в и из правил, можно хранить данные в `TransactionContext`. Это просто словарь, который поддерживается во время транзакции. Он удаляется при завершении транзакции. Аргументы события в каждом правиле предоставляют доступ к нему. Помните, что правила не выполняются в определенном порядке.  
  
7.  После учета других альтернативных систем, используйте правила. Например если вы хотите обновить при изменении значения свойства, рассмотрите возможность использования вычисляемого свойства. Если требуется ограничить размер или расположение фигуры, используйте `BoundsRule`. Если необходимо реагировать на изменение значения свойства, добавьте `OnValueChanged` обработчик к свойству. Для получения дополнительной информации см. [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md).  
  
## Пример  
 В следующем примере обновляется свойство при создании экземпляра доменной связи для связи двух элементов. Правило будет применяться не только в том случае, когда пользователь создает ссылку на схему, а также если программный код создает ссылку.  
  
 Чтобы протестировать этот пример, создайте DSL с помощью шаблона решения поток задач и вставьте следующий код в файл в проекте Dsl. Построение и запустите решение и открыть образец файла в проект "Отладка". Нарисуйте комментарий связь между фигуры комментария и элемент потока. Изменения текста в комментарий в отчет последнего элемента, его подключения.  
  
 На практике обычно было бы создавать DeleteRule для каждого методы AddRule.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## См. также  
 [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Класс BoundsRules ограничивает расположение и размеры фигур](../modeling/boundsrules-constrain-shape-location-and-size.md)