---
title: Связывание обновлений модели UML с помощью транзакций | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657606"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Связывание обновлений модели UML с использованием транзакций
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При определении расширения для конструкторов UML в Visual Studio можно сгруппировать несколько изменений в одну транзакцию, называемую *связанным контекстом отмены*. Чтобы узнать, какие версии Visual Studio поддерживают модели UML, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 По умолчанию пользователь может по отдельности отменять каждое изменение, которое ваш код вносит в модель. Например, если вы определяете команду меню, которая меняет местами названия двух классов UML, пользователь может вызвать эту команду и затем выполнить одну операцию отмены. Приведет к отмене изменения только для для одного имени из двух, в результате чего модель будет находиться в непредвиденном состоянии.

 Чтобы избежать этого, код может выполнить серию изменений в пределах одной транзакции. В результате пользователь будет воспринимать эти изменения как одно изменение. Последующее выполнение команды отмены приведет к отмене всей серии изменений.

 Дополнительным преимуществом является то, что код может отменить частично выполненный набор изменений путем создания исключения или прерывания транзакции.

## <a name="to-group-changes-into-a-single-transaction"></a>Группировка изменений в одну транзакцию
 Убедитесь, что ссылки проекта включают в себя следующую сборку .NET.

 **Microsoft. VisualStudio. моделирования. SDK. [версия]. dll**

 Внутри класса объявите импортированное свойство с типом <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 В методе, изменяющем модель, заключите изменения в транзакцию:

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 Обратите внимание на следующее.

- Необходимо всегда включать `Commit()` в конце транзакции. В случае ликвидации транзакции без фиксации выполняется ее откат. То есть модель будет восстановлена в том состоянии, которое предшествовало началу транзакции.

- Если возникает исключение, не перехватываемое внутри транзакции, выполняется ее откат. Часто блок `using` транзакции заключается внутрь блока `try…catch`.

- Вы можете вкладывать транзакции.

- Для `BeginTransaction()` можно указать любое непустое имя.

- Эти транзакции затрагивают только хранилище моделей UML. Транзакции моделирования не затрагивают следующее: переменные, внешние хранилища, такие как файлы и базы данных, схемы слоев и модели кода.

## <a name="example"></a>Пример

```
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Interfaces;
    using Microsoft.VisualStudio.Uml.Classes;
    using Microsoft.VisualStudio.Uml.Extensions;
    using System.Linq;
    using System.ComponentModel.Composition;
 ...
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  public void Execute(IMenuCommand command)
  {
    var selectedShapes =
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;
    string firstName = firstElement.Name;
    // Perform changes inside a transaction so that undo
    // works as a single change.
    using (ILinkedUndoTransaction transaction =
      LinkedUndoContext.BeginTransaction("Swap names"))
    {
        firstElement.Name = lastElement.Name;
        lastElement.Name = firstName;
        transaction.Commit();
    }
 }
```

## <a name="see-also"></a>См. также:
 [Программирование с помощью API UML](../modeling/programming-with-the-uml-api.md) [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md)
