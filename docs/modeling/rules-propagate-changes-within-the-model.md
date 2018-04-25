---
title: Правила распространяют изменения в пределах модели
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2c0490e69ef63dc109ef0563d27a6412f7b54746
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>Правила распространяют изменения в пределах модели
Можно создать правило хранилища для распространения изменений от одного элемента к другому в визуализации и моделирования SDK (VMSDK). При изменении любого элемента в хранилище правил планируются для выполнения, обычно в том случае, если внешняя транзакция фиксируется. Существуют различные типы правил для различных типов событий, таких как элемент добавляется или удаляется. Правила можно присоединить к определенным типам элементов, фигуры или схемы. Многие встроенные функции определяются правилами: например, правила обеспечивают, диаграммы обновляются при изменении модели. Доменный язык можно настроить путем добавления собственных правил.

 Сохранить правила особенно полезны для распространения изменений в хранилище — то есть, примет элементы модели, связи, фигуры или соединителей и своего домена свойства. Правила не выполняются при вызове пользователем команды отмены или повтора. Вместо этого диспетчер транзакций гарантирует, что содержимое хранилища будут восстановлены в состоянии. Если вы хотите распространить изменения к ресурсам за пределами магазина, используйте хранения события. Дополнительные сведения см. в разделе [обработчики распространение изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Например предположим, что вы хотите указать, что всякий раз, когда пользователь (или код) создает новый элемент типа ExampleDomainClass, дополнительный элемент другого типа создается в другой части модели. Можно написать методы AddRule и связать его с ExampleDomainClass. Можно написать код, в правило, чтобы создать дополнительный элемент.

```csharp
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

    // Code here propagates change as required - for example:
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
>  Код правила следует изменить состояние только элементов в хранилище; то есть правило следует изменять только элементы модели, связи, фигур, соединители, схемы или их свойства. Если требуется распространение изменений к ресурсам за пределами хранилища определяют хранения события. Дополнительные сведения см. в разделе [обработчики распространение изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Чтобы определить правила

1.  Определите правило, как класс с префиксом `RuleOn` атрибута. Атрибут связывает правило с одним из вашего домена классы, связи или диаграммы. Правило будет применяться к каждому экземпляру этого класса, который может быть абстрактным.

2.  Зарегистрировать правило, добавьте его в набор, возвращаемый `GetCustomDomainModelTypes()` в классе модели домена.

3.  Производный класс правило из одного абстрактных классов правило и написать код метода выполнения.

 В следующих разделах описаны эти шаги более подробно.

### <a name="to-define-a-rule-on-a-domain-class"></a>Чтобы определить правила для класса домена

-   В файле пользовательского кода, определение класса и перед ними <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> атрибута:

    ```
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

-   Тип субъекта в качестве первого параметра может быть класс домена, доменной связи, фигуры, соединителя или схемы. Как правило применяются правила для домена классы и отношения.

     `FireTime` Обычно `TopLevelCommit`. Это гарантирует, что правило выполняется только после внесения всех основные изменения транзакции. Являются встроенными, которое выполняет правила, вскоре после изменения; и LocalCommit, в котором выполняется правило, в конце текущей транзакции (что может оказаться самым внешним). Можно также задать приоритет правила влияет на порядок в очереди, но это метод ненадежной достижения результата, который требуется.

-   Абстрактный класс можно указать в качестве типа субъекта.

-   Правило применяется ко всем экземплярам класса субъекта.

-   Значение по умолчанию `FireTime` — TimeToFire.TopLevelCommit. В этом случае правило должно выполняться при фиксации внешней транзакции. Альтернативой является TimeToFire.Inline. В этом случае правило должно выполняться после запускающее событие.

### <a name="to-register-the-rule"></a>Чтобы зарегистрировать правило

-   Добавьте правило класс к списку типов возвращаемых `GetCustomDomainModelTypes` в модели домена:

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

-   Если вы не уверены в правильности имени класса модели домена, найдите в файле **Dsl\GeneratedCode\DomainModel.cs**

-   Записать этот код в файле пользовательского кода в проекте DSL.

### <a name="to-write-the-code-of-the-rule"></a>Написание кода правила

-   Создайте правило класс, производный от одного из следующих базовых классов:

    |Базовый класс|Триггер|
    |----------------|-------------|
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Добавлен элемент, ссылку или фигуры.<br /><br /> Используется для обнаружения новых связей, помимо новые элементы.|
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|При изменении значения свойства домена. Аргумент метода содержит старое и новое значения.<br /><br /> Для фигур-это правило срабатывает при встроенной `AbsoluteBounds` изменения свойств, при перемещении фигуры.<br /><br /> Во многих случаях он является более удобным для переопределения `OnValueChanged` или `OnValueChanging` в обработчике свойство. Эти методы вызываются непосредственно перед и после изменения. В отличие от этого правила обычно выполняется в конце транзакции. Дополнительные сведения см. в разделе [обработчики изменений значений свойств домена](../modeling/domain-property-value-change-handlers.md). **Примечание:** это правило не срабатывает при создании или удалении ссылки. Вместо этого запись `AddRule` и `DeleteRule` для доменной связи.|
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Запускается при элемента или связи — для удаления. Свойство ModelElement.IsDeleting имеет значение true, до конца транзакции.|
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Выполняется при удалении элемента или связи. Правило выполняется после выполнены другие правила, включая DeletingRules. ModelElement.IsDeleting имеет значение false, а ModelElement.IsDeleted имеет значение true. Чтобы разрешить последующие отмены, элемент фактически не удаляется из памяти, но он удаляется из Store.ElementDirectory.|
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Элемент перемещается из секции одного хранилища в другое.<br /><br /> (Обратите внимание, что это не связано с графический положения фигуры).|
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Это правило применяется только к отношений между доменами. Он срабатывает, если явно назначить элемента модели на любом конце ссылки.|
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Запускается, когда порядок ссылок на статью или из элемента изменяется с помощью методов MoveBefore или MoveToIndex связи.|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Выполняется при создании транзакции.|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Выполняется, когда транзакция будет зафиксирована.|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Выполнен, когда будет выполнен откат транзакции.|

-   Каждый класс имеет метод, который можно переопределить. Тип `override` в классе для его обнаружения. Параметр этого метода определяет элемент, которое необходимо изменить.

 Обратите внимание на следующие аспекты правила:

1.  Набор изменений в транзакции может привести к запуску много правил. Как правило правила выполняются при фиксации внешней транзакции. Они выполняются в неопределенном порядке.

2.  Правило всегда выполняется внутри транзакции. Таким образом не нужно создать новую транзакцию для внесения изменений.

3.  Правила не выполняются, когда производится откат транзакции, или при выполнении операций отмены или повтора. Эти операции сбросить все содержимое хранилища в предыдущее состояние. Таким образом Если правило изменяет состояние любых данных за пределы хранилища, он может не Имейте в synchronism с хранилищем содержимого. Чтобы обновить состояние за пределы хранилища, лучше использовать события. Дополнительные сведения см. в разделе [обработчики распространение изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4.  Некоторые правила, выполняются при загрузке модели из файла. Чтобы определить, является ли загрузки и сохранения в данный момент, используйте `store.TransactionManager.CurrentTransaction.IsSerializing`.

5.  Если правила создается несколько триггеров правило, они будут добавлены в конец списка срабатывание и будет выполняться до завершения транзакции. DeletedRules выполняются после всех остальных. Одно правило можно запускать несколько раз в транзакции, один раз для каждого изменения.

6.  Для передачи информации в и из правил, можно хранить данные в `TransactionContext`. Это просто словарь, который поддерживается во время транзакции. Он удаляется после завершения транзакции. Аргументы события в каждом правиле обеспечить доступ к нему. Помните, что правила не выполняются в определенном порядке.

7.  Использовать правила после учета другие альтернативные элементы. Например если вы хотите обновить при изменении значения свойства, рассмотрите возможность использования вычисляемого свойства. Если вы хотите ограничить размер или расположение фигуры, используйте `BoundsRule`. Если необходимо реагировать на изменение значения свойства, добавьте `OnValueChanged` обработчика к свойству. Дополнительные сведения см. в разделе [распространение изменений и реагирование на](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Пример
 В следующем примере обновляется свойство при создании экземпляра доменной связи для связи двух элементов. Правило будет применяться не только в том случае, когда пользователь создает ссылку на схему, а также если программный код создает ссылку.

 Чтобы протестировать этот пример, создайте DSL, с помощью шаблона решения задач потока и вставьте следующий код в файл в проект Dsl. Построить и запустить решение и открыть образец файла в проекте отладка. Нарисуйте связь комментария между фигуры комментария и элемент потока. Изменения текста в комментарий к отчету последнего элемента, его для подключения.

 На практике обычно пишете DeleteRule для каждого методы AddRule.

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

## <a name="see-also"></a>См. также

- [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md)
- [Класс BoundsRules ограничивает расположение и размеры фигур](../modeling/boundsrules-constrain-shape-location-and-size.md)