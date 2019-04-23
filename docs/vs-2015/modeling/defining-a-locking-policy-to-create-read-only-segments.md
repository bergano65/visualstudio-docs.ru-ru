---
title: Определение политики блокировки для создания сегментов, доступных только для чтения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed3eeb8e2907eb71a75884a19f174774055783c4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062247"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Определение политики блокировки для создания сегментов, доступных только для чтения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

API неизменности [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK дает возможность программе блокировки всех или части модели доменного языка (DSL), чтобы его можно читать но не изменяется. Этот параметр только для чтения может использоваться, например, таким образом, пользователь может запросить коллеги аннотировать и просматривать модель DSL, но запретить их изменять исходный.  
  
 Кроме того, как автор доменного языка с, можно определить *политика блокировки.* Политики блокировки определяет, какие виды блокировок разрешено, запрещено или обязательным. Например при публикации DSL, могут потребовать сторонних разработчиков, расширить ее с помощью новых команд. Но можно также использовать политики блокировки для предотвращения их изменений состояния только для чтения указанные части модели.  
  
> [!NOTE]
>  Политики блокировки можно обойти с помощью отражения. Он предоставляет четкой границы для сторонних разработчиков, но не обеспечивают надежную защиту.  
  
 Дополнительные сведения и примеры можно найти по адресу [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) веб-сайта.  
  
## <a name="setting-and-getting-locks"></a>Задание и получение блокировки  
 Можно задать блокировки на хранилище, в раздел или на отдельном элементе. Например Эта инструкция будет предотвратить удаление элемента модели и также предотвратит ее свойства изменяемой:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Другие значения блокировки могут использоваться для предотвращения изменения связей, создания элемента, перемещение между секций, а также повторно упорядочивания ссылки в роли.  
  
 Блокировки применяются как на действия пользователя, так и в код программы. Попытка внести изменения, программный код `InvalidOperationException` будет создано. Блокировки учитываются в операции отмены или повтора.  
  
 Можно определить, имеет ли элемент любые блокировки в заданном наборе с помощью `IsLocked(Locks)` и текущего набора блокировок на элементе можно получить с помощью `GetLocks()`.  
  
 Можно задать блокировку без использования транзакции. Блокировка базы данных не является частью хранилища. Если вы установите блокировку в ответ на изменение значения в хранилище, например в OnValueChanged, следует разрешить изменения, которые являются частью операции отмены.  
  
 Эти методы являются методами расширения, которые определены в <xref:Microsoft.VisualStudio.Modeling.Immutability> пространства имен.  
  
### <a name="locks-on-partitions-and-stores"></a>Блокировок на разделы и хранилищ  
 Блокировки могут также применяться для секций и хранилище. Блокировку, которая задается в разделе применяется ко всем элементам в секции. Таким образом например, следующая инструкция будет препятствовать все элементы в секции их удалении, независимо от состояния свои собственные блокировки. Тем не менее, других блокировок например `Locks.Property` по-прежнему может устанавливаться на отдельные элементы:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Блокировка, устанавливаемая на Store применяется ко всем его элементам, независимо от параметров блокировки на секции, а также элементы.  
  
### <a name="using-locks"></a>Использование блокировок  
 Блокировки можно использовать для реализации схем, как в следующих примерах:  
  
- Запрет изменений ко всем элементам и связей, за исключением тех, которые представляют комментарии. Это позволяет пользователям для добавления заметок к модели, не изменяя его.  
  
- Запрет изменений в раздел по умолчанию, но разрешить изменения в схеме секционирования. Пользователь может изменить эту схему, но невозможно изменить базовую модель.  
  
- Запрет изменений в Store, за исключением группы пользователей, зарегистрированных в отдельной базе данных. Для других пользователей схема и модели доступны только для чтения.  
  
- Запретить изменения модели, если логическое свойство схемы устанавливается в значение true. Укажите команду меню, чтобы изменить это свойство. Это позволяет обеспечить пользователям, не выполняющие изменяет случайно.  
  
- Запрет добавления и удаления элементов и связей определенного класса, но разрешить изменения свойств. Это предоставляет пользователям основные формы, в котором он может заполнить свойства.  
  
## <a name="lock-values"></a>Значения блокировки  
 Блокировки можно задать в Store, раздел или отдельных ModelElement. Блокирует `Flags` перечисления: можно объединить его значения, с помощью "&#124;".  
  
- Блокировки элемента ModelElement всегда включать блокировки его секции.  
  
- Блокировки секции всегда включать блокировки Store.  
  
  Нельзя установить блокировку на секции или хранить и в то же время отключить блокировку отдельного элемента.  
  
|Значение|То есть если `IsLocked(Value)` имеет значение true|  
|-----------|------------------------------------------|  
|Нет|Без ограничений.|  
|Свойство|Невозможно изменить свойства домена элементов. Это не относится к свойствам, создаваемых ролью доменного класса в связи.|  
|Add|Новые элементы и ссылки не могут создаваться в секции или хранения.<br /><br /> Неприменимо к `ModelElement`.|  
|Перемещение|Элемент нельзя перемещать между секциями, если `element.IsLocked(Move)` имеет значение true, или если `targetPartition.IsLocked(Move)` имеет значение true.|  
|Оператор delete|Невозможно удалить элемент, если эта блокировка устанавливается в самом элементе или в любых элементов, к которому будет распространять удаления, такие как внедренные элементы и фигуры.<br /><br /> Можно использовать `element.CanDelete()` для обнаружения, может ли быть удален элемент.|  
|Изменение порядка|Невозможно изменить порядок ссылок в исполнителя роли.|  
|Исполнитель роли|Набор ссылок, определяемые в этот элемент нельзя изменить. Например новые элементы не могут быть внедрены в этом элементе. Это не влияет на ссылки, для которой этот элемент является целевым объектом.<br /><br /> Если этот элемент представляет собой ссылку, ее исходных и целевых не затрагиваются.|  
|Все|Побитовая операция или для других значений.|  
  
## <a name="locking-policies"></a>Политики блокировки  
 Как автор доменного языка с, можно определить *политика блокировки*. Политики блокировки moderates операцию SetLocks(), таким образом, вы можете запретить конкретные блокировки, задать или требует, что конкретные блокировки должен быть установлен. Как правило, используется политики блокировки убедить пользователей и разработчиков из случайно contravening предполагаемого использования доменного языка с таким же образом, что можно объявить переменную `private`.  
  
 Также можно использовать политики блокировки, установка блокировки для всех элементов в зависимости от типа элемента. Это обусловлено `SetLocks(Locks.None)` вызывается всегда, когда элемент сначала создается или десериализован из файла.  
  
 Тем не менее нельзя использовать политику для изменения блокировки с элемента во время его жизненного цикла. Для достижения этого эффекта следует использовать вызовы `SetLocks()`.  
  
 Определение политики блокировки, необходимо выполнить следующее:  
  
- Создайте класс, реализующий <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
- Добавьте этот класс службы, которые доступны через DocData вашего DSL.  
  
### <a name="to-define-a-locking-policy"></a>Определение политики блокировки  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> имеет следующее определение:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Эти методы вызываются в том случае, когда выполняется вызов `SetLocks()` в Store, раздел или ModelElement. В каждом методе вам будет предоставлен набора предложенных блокировок. Может возвращать предложенное набора, или можно добавлять и удалять блокировки.  
  
 Пример:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Чтобы убедиться в том, что пользователи всегда могут удалять элементы, даже если другой код вызывает `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Чтобы запретить все свойства каждого элемента класса MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Чтобы привести политику доступно в виде службы  
 В вашей `DslPackage` проект, добавить новый файл, который содержит код, аналогичный приведенному ниже:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```
