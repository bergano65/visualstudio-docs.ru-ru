---
title: "Обработчики изменений значений свойств доменов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Доменный язык, переопределение обработчиков событий"
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Обработчики изменений значений свойств доменов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Когда в доменном языке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] меняется свойство домена, в обработчике свойства домена вызываются методы `OnValueChanging()` и `OnValueChanged()`.  Чтобы отреагировать на внесенное изменение, можно переопределить эти методы.  
  
## Переопределение методов обработчика свойства  
 Каждое свойство домена вашего доменного языка обрабатывается классом, вложенным в родительский класс домена.  Его имя имеет следующий формат: *ИмяСвойства*PropertyHandler.  Проверить этот класс обработчика свойств можно в файле **Dsl\\Generated Code\\DomainClasses.cs**.  В этом классе непосредственно перед изменением значения вызывается метод `OnValueChanging()`, а сразу после изменения — метод `OnValueChanged()`.  
  
 Предположим, у вас есть класс домена с именем `Comment`, у которого имеется строковое свойство домена с именем `Text` и целочисленное свойство с именем `TextLengthCount`.  Чтобы свойство `TextLengthCount` всегда содержало длину сроки `Text`, необходимо написать в отдельном файле проекта Dsl следующий код:  
  
```  
// Domain Class "Comment":  
public partial class Comment   
{  
  // Domain Property "Text":  
  partial class TextPropertyHandler  
  {  
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)  
    {  
      base.OnValueChanging(element, oldValue, newValue);  
  
      // To update values outside the Store, write code here.  
  
      // Let the transaction manager handle undo:  
      Store store = element.Store;  
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;  
  
      // Update values in the Store:  
      this.TextLengthCount = newValue.Length;  
    }  
  }  
}  
  
```  
  
 Об обработчиках свойств необходимо помнить следующее.  
  
-   Методы обработчика свойств вызываются, когда пользователь вносит изменения в свойство домена, а также когда код программы назначает свойству другое значение.  
  
-   Методы вызываются, только когда значение действительно меняется.  Обработчик не вызывается, если код программы назначает значение, равное текущему.  
  
-   Вычисляемые и пользовательские свойства доменов хранения не имеют методов OnValueChanged и OnValueChanging.  
  
-   Обработчик изменений нельзя использовать для изменения нового значения.  Если это необходимо, например для ограничения значения в определенном диапазоне, определите правило `ChangeRule`.  
  
-   Обработчик изменений нельзя добавить в свойство, представляющее роль отношения.  Вместо этого настройте правила `AddRule` и `DeleteRule` в классе отношения.  Они запускаются, когда связи создаются или изменяются.  Для получения дополнительной информации см. [Правила распространяют изменения в пределах модели](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Изменения внутри хранилища и за его пределами  
 Методы обработчика свойств вызываются внутри транзакции, запустившей изменение.  Это значит, что можно внести и другие изменения в хранилище, не открывая новую транзакцию.  Изменения могут привести к дополнительным вызовам обработчика.  
  
 Когда транзакция отменяется, выполняется заново или откатывается, вносить изменения в хранилище, то есть в элементы модели, отношения, фигуры, схемы соединителей или их свойства, не нужно.  
  
 Более того, обновлять значения не нужно и тогда, когда модель загружается из файла.  
  
 Изменения в модели следует защищать тестом следующего вида:  
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 Если же обработчик свойств распространяет изменения за пределы хранилища, например в файл, базу данных или переменные вне хранилища, эти изменения обязательно необходимо внести и обеспечить обновление внешних значений при выполнении операций отмены или повторного выполнения.  
  
### Отмена изменения  
 Если изменение необходимо предотвратить, можно откатить текущую транзакцию.  Это позволит, например, гарантировать, что свойство остается в определенном диапазоне.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### Альтернативный способ: вычисляемые свойства  
 В предыдущем примере показано, как использовать метод OnValueChanged\(\) для распространения значений из одного свойства домена в другое.  Каждое свойство имеет свое сохраненное значение.  
  
 Вместо этого можно определить в качестве вычисляемого производное свойство.  В этом случае свойство не имеет собственного хранилища, а определяющая функция оценивается там, где это значение требуется.  Для получения дополнительной информации см. [Вычисляемые и пользовательские свойства хранилища](../modeling/calculated-and-custom-storage-properties.md).  
  
 Вместо использования кода в предыдущем примере можно присвоить полю **Kind** параметра `TextLengthCount` значение **Calculated** в определении доменного языка.  Для этого свойства домена нужно предоставить собственный метод **Get**.  Метод **Get** возвращает текущую длину строки `Text`.  
  
 Потенциальный недостаток вычисляемых свойств заключается в том, что выражение оценивается при каждом использовании значения, что может снижать производительность.  Также к вычисляемым свойствам не применяются методы OnValueChanging\(\) и OnValueChanged\(\).  
  
### Альтернативный способ: метод ChangeRule  
 Если метод ChangeRule определен, он выполняется в конце транзакции, изменяющей значение свойства.  Для получения дополнительной информации см. [Правила распространяют изменения в пределах модели](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Если в одной транзакции вносятся сразу несколько изменений, метод ChangeRule выполняется после их завершения.  В отличие от него методы OnValue...  выполняются, если какие\-то изменения не внесены.  В зависимости от целей метод ChangeRule может оказаться более подходящим.  
  
 ChangeRule можно также использовать для корректировки нового значения свойства, чтобы сохранить его в определенном диапазоне.  
  
> [!WARNING]
>  Если правило вносит изменения в содержимое хранилища, могут запускаться другие правила и обработчики свойства.  Если правило изменяет свойство, которое его запустило, оно будет вызвано вновь.  Обязательно следите за тем, чтобы определения правил не приводили к бесконечному запуску.  
  
```  
using Microsoft.VisualStudio.Modeling;   
...  
// Change rule on the domain class Comment:  
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]   
class MyCommentTrimRule : ChangeRule  
{  
  public override void   
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
  {  
    base.ElementPropertyChanged(e);  
    Comment comment = e.ModelElement as Comment;  
  
    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))  
      comment.Text = comment.Text.Trim();  
    // If changed, rule will trigger again.  
  }  
}  
  
// Register the rule:   
public partial class MyDomainModel   
{  
 protected override Type[] GetCustomDomainModelTypes()   
 { return new Type[] { typeof(MyCommentTrimRule) };   
 }  
}  
  
```  
  
## Пример  
  
### Описание  
 Код в приведенном ниже примере переопределяет обработчик свойств домена и уведомляет пользователя об изменении свойства класса домена `ExampleElement`.  
  
### Код  
  
```  
using DslModeling = global::Microsoft.VisualStudio.Modeling;  
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;  
  
namespace msft.FieldChangeSample  
{  
  public partial class ExampleElement  
  {  
    internal sealed partial class NamePropertyHandler  
    {  
      protected override void OnValueChanged(ExampleElement element,  
         string oldValue, string newValue)  
      {  
        if (!this.Store.InUndoRedoOrRollback)  
        {  
           // make in-store changes here...  
        }  
        // This part is called even in undo:  
        System.Windows.Forms.MessageBox.Show("Value Has Changed");  
        base.OnValueChanged(element, oldValue, newValue);  
      }  
    }  
  }  
}  
```  
  
## См. также  
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanged%2A>   
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanging%2A>