---
title: Правила распространяют изменения в пределах модели
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f61c9623cd2006f0df82c93dc420a25f23d3d2a
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416215"
---
# <a name="rules-propagate-changes-within-the-model"></a>Правила распространяют изменения в пределах модели
Можно создать правило магазина для распространения изменений от одного элемента к другому в визуализации и пакет SDK для моделирования (VMSDK). При внесении изменений к любому элементу в Store, правила планируются для выполнения, обычно в том случае, когда фиксируется в самой внешней транзакции. Существуют различные типы правил для различных видов событий, таких как добавление элемента, или удалить его. Правила можно присоединить к определенным типам элементов, фигур или схем. Многие встроенные функции определяются правилами сбора данных: например, правила гарантируют, что схема обновляется при изменении модели. Доменный язык можно настроить путем добавления собственных правил.

 Правила Store особенно полезны, распространение изменений в хранилище — то есть изменений в элементы модели, отношения, фигуры или соединители и их домена свойства. Правила не выполняются при вызове пользователем команды отмены или повтора. Вместо этого диспетчер транзакций гарантирует, что содержимое хранилища восстанавливаются в правильном состоянии. Если вы хотите распространить изменения к ресурсам за пределами хранилища, используйте Store события. Дополнительные сведения см. в разделе [обработчики распространения изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Например предположим, что вы хотите указать, что каждый раз, когда пользователь (или код) создает новый элемент типа ExampleDomainClass, дополнительный элемент другого типа создается в другой части модели. Можно написать AddRule и связать его с ExampleDomainClass. Можно написать код в правило, чтобы создать дополнительный элемент.

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
>  Код правила следует изменить состояние только элементов внутри Store; то есть правила следует изменять только элементы модели, отношения, фигуры, соединители, схемы или их свойства. Если вы хотите распространить изменения к ресурсам за пределами хранилища, определяют Store события. Дополнительные сведения см. в разделе [обработчики распространения изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Определение правила

1. Определить правила, как класс начинаются с префикса `RuleOn` атрибута. Этот атрибут связывает правило с помощью одного из классов доменов, связи или элементов схемы. Правило будет применяться к каждому экземпляру этого класса, который может быть абстрактным.

2. Зарегистрировать правило, добавьте его в наборе, возвращаемом `GetCustomDomainModelTypes()` в классе модели домена.

3. Производного класса правило абстрактных классов правило и написать код в метод выполнения.

   В следующих разделах эти шаги более подробно.

### <a name="to-define-a-rule-on-a-domain-class"></a>Чтобы определить правила для класса домена

-   В файле пользовательского кода, определите класс и перед ними <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> атрибут:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

-   Тип субъекта в качестве первого параметра может быть класс домена, доменного отношения, фигуры, соединителя или схемы. Как правило применяются правила для классов доменов и отношений.

     `FireTime` Обычно `TopLevelCommit`. Это гарантирует, что это правило выполняется только в том случае, после внесения всех основные изменения транзакции. Являются встроенными, то есть выполняется правило после ее завершения; и LocalCommit, который выполняет правила в конце текущей транзакции (это не может быть внешний). Можно также задать приоритет правила, которое влияет на порядок в нем в очереди, но это метод ненадежной достижения результата, который требуется.

-   Абстрактный класс можно указать в качестве типа субъекта.

-   Правило применяется ко всем экземплярам класса субъекта.

-   Значение по умолчанию для `FireTime` является TimeToFire.TopLevelCommit. В результате правило для выполнения при фиксации внешней транзакции. Альтернативным вариантом является TimeToFire.Inline. В результате правило для выполнения сразу же после события-триггера.

### <a name="to-register-the-rule"></a>Чтобы зарегистрировать правило

-   Добавить правило в список типов, возвращенного методом `GetCustomDomainModelTypes` в вашей модели предметной области:

    ```csharp
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

-   Если вы не уверены в правильности имени класса модели домена, заглянем в файле **Dsl\GeneratedCode\DomainModel.cs**

-   Написать следующий код в файле пользовательского кода в проекте DSL.

### <a name="to-write-the-code-of-the-rule"></a>Чтобы написать код правила

- Наследуйте класс правило из одного из следующих базовых классов:


  | Базовый класс | Триггер |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Добавляется элемент, ссылку или фигуры.<br /><br /> Позволяет обнаруживать новые связи, а также новые элементы. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Значение свойства домена изменяется. Аргумент метода предоставляет старое и новое значения.<br /><br /> Для фигур, это правило срабатывает при встроенной `AbsoluteBounds` изменения свойств, при перемещении фигуры.<br /><br /> Во многих случаях более удобно для переопределения `OnValueChanged` или `OnValueChanging` в обработчике свойств. Эти методы вызываются непосредственно перед и после изменения. В отличие от этого правила обычно выполняется в конце транзакции. Дополнительные сведения см. в разделе [обработчики изменений значений свойств доменов](../modeling/domain-property-value-change-handlers.md). **Примечание.**  Это правило не срабатывает при создании или удалении ссылки. Вместо этого запись `AddRule` и `DeleteRule` для доменной связи. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Запускается при элемента или ссылки для удаления. Свойство ModelElement.IsDeleting имеет значение true, до конца транзакции. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Выполнить удаление элемента или ссылки. Это правило выполняется после создания всех остальных правил, включая DeletingRules. ModelElement.IsDeleting значение false, а ModelElement.IsDeleted имеет значение true. Чтобы разрешить последующие отмены, элемент фактически не удаляется из памяти, но он удаляется из Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Элемент перемещается из одного хранилища секции в другую.<br /><br /> (Обратите внимание на то, что это не связано с графический положения фигуры). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Это правило применяется только к доменных связей. Оно активируется, если явно назначить элемент модели в любой конец ссылку. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Активируется, когда порядок ссылок на статью или из элемента изменяется с помощью методов MoveBefore или MoveToIndex по ссылке. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Выполняется при создании транзакции. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Запускаются, когда транзакция будет зафиксирована. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Выполняется при транзакции является откат. |


- Каждый класс имеет метод, который можно переопределить. Тип `override` в классе для его обнаружения. Параметр этого метода определяет элемент, которого необходимо изменить.

  Обратите внимание на следующие моменты, о правилах:

1.  Набор изменений в транзакции может вызвать много правил. Как правило правила выполняются при фиксации внешней транзакции. Они выполняются в неопределенном порядке.

2.  Правило всегда выполняться внутри транзакции. Таким образом вы не создавая новую транзакцию для внесения изменений.

3.  Правила не выполняются при откате транзакции, или при выполнении операций отмены или повтора. Эти операции сбросить все содержимое Store в предыдущее состояние. Таким образом Если правило изменяет состояние объекты вне Store, он может не поддерживать в synchronism с Store содержимого. Чтобы обновить состояние за пределами Store, лучше использовать события. Дополнительные сведения см. в разделе [обработчики распространения изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4.  Некоторые правила выполняются в том случае, когда модель загружается из файла. Чтобы определить, является ли ход выполнения загрузки или сохранения, используйте `store.TransactionManager.CurrentTransaction.IsSerializing`.

5.  Если правила создается несколько триггеров правило, они будут добавляться в конец списка срабатывание и будет выполнен до завершения транзакции. DeletedRules выполняются после всех остальных. Одно правило может выполняться много раз в транзакции, один раз для каждого изменения.

6.  Для передачи информации в и из правила, можно хранить сведения в `TransactionContext`. Это просто dictionary, сохраняемую в ходе транзакции. Он удаляется при завершении транзакции. Аргументы события в каждом правиле обеспечить доступ к нему. Помните, что правила не выполняются в определенном порядке.

7.  Используйте правила после рассмотрения другие альтернативные элементы. Например если вы хотите обновить при изменении значения свойства, рассмотрите возможность использования вычисляемое свойство. Если вы хотите ограничить размер или расположение фигуры, используйте `BoundsRule`. В ответ на изменение значения свойства следует добавить `OnValueChanged` обработчик к свойству. Дополнительные сведения см. в разделе [реагирование на события и распространение изменений](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Пример
 В следующем примере обновляется свойство, при создании экземпляра доменной связи для связи двух элементов. Правило будет применяться не только в том случае, когда пользователь создает ссылку на схему, а также если программный код создает ссылку.

 Чтобы протестировать этот пример, создайте DSL с помощью шаблона решения потока задачи и вставьте следующий код в файле в проекте Dsl. Построить и запустить решение и откройте пример файла в проект "Отладка". Нарисуйте связь комментарий между фигуры комментария и элемент нефиксированного формата. В комментарий к отчету, для последнего элемента, который вы подключили его к текст.

 На практике вы обычно написали DeleteRule для каждого AddRule.

```csharp
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