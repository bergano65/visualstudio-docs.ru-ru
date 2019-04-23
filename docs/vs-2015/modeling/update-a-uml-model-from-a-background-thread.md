---
title: Обновление модели UML из фонового потока | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d5a7ad318b5bd9fac41d5e8835169e4075d1da67
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093011"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Обновление модели UML из фонового потока
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Иногда бывает полезно вносить изменения в модель в фоновом потоке. Например, при загрузке сведений из медленного внешнего ресурса можно использовать фоновый поток для контроля обновлений. Это позволит пользователю видеть обновления по мере их появления.  
  
 Однако следует помнить, что хранилище UML не является потокобезопасным. Важно принять указанные ниже меры предосторожности.  
  
- Каждое обновление модели или схемы должно выполняться в потоке пользовательского интерфейса. Фоновый поток должен использовать метод <xref:System.Windows.Forms.Control.Invoke%2A> или `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A>, чтобы поток пользовательского интерфейса выполнил текущие обновления.  
  
- При группировке последовательности изменений в одной транзакции рекомендуется исключить для пользователя возможность изменять модель во время выполнения транзакции. В противном случае все изменения, совершенные пользователем, станут частью одной транзакции. Предотвратить вмешательство пользователя можно, вызвав модальное диалоговое окно. Можно предоставить в диалоговом окне кнопку "Отмена". Пользователь может видеть изменения по мере того, как они происходят.  
  
## <a name="example"></a>Пример  
 В этом примере используется фоновый поток для внесения нескольких изменений в модель. Диалоговое окно используется, чтобы исключить вмешательство пользователя во время работы потока. В этом простом примере диалоговое окно не содержит кнопки "Отмена". Однако добавить эту функцию несложно.  
  
#### <a name="to-run-the-example"></a>Запуск примера  
  
1. Создайте обработчик команд в проекте C#, как описано в разделе [определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Убедитесь в том, что проект включает ссылки на следующие сборки:  
  
   - Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   - Microsoft.VisualStudio.Modeling.Sdk.[версия]  
  
   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[версия]  
  
   - Microsoft.VisualStudio.Uml.Interfaces  
  
   - System.ComponentModel.Composition  
  
   - System.Windows.Forms.  
  
3. Добавьте в проект форму Windows с именем **ProgressForm**. Она должна показывать сообщение о том, что идет процесс обновления. Она не должна содержать других элементов управления.  
  
4. Добавьте файл C#, содержащий код, приведенный после шага 7.  
  
5. Постройте и запустите проект.  
  
    Новый экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запустится в экспериментальном режиме.  
  
6. Создайте или откройте схему классов UML в экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Щелкните правой кнопкой мыши в схеме классов UML и нажмите кнопку **добавить несколько классов UML**.  
  
   Несколько новых полей классов отобразится на схеме один за другим с интервалом в полсекунды.  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.ComponentModel.Composition;  
using System.Threading;  
using System.Windows.Forms;  
  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.Uml.Classes;  
  
namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class UmlClassAdderCommand : ICommandExtension  
  {  
  
    [Import]  
    IDiagramContext context { get; set; }  
  
    [Import]  
    ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called when the user runs the command.  
    public void Execute(IMenuCommand command)  
    {  
      // The form that will exclude the user.  
      ProgressForm form = new ProgressForm();  
  
      // System.ComponentModel.BackgroundWorker is a  
      // convenient way to run a background thread.  
      BackgroundWorker worker = new BackgroundWorker();  
      worker.WorkerSupportsCancellation = true;  
  
      worker.DoWork += delegate(object sender, DoWorkEventArgs args)  
      {  
        // This block will be executed in a background thread.  
  
        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;  
        IModelStore store = diagram.ModelStore;  
        const int CLASSES_TO_CREATE = 15;  
  
        // Group all the changes together.  
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))  
        {  
          for (int i = 1; i < CLASSES_TO_CREATE; i++)  
          {  
            if (worker.CancellationPending)   
               return; // No commit - undo all.  
  
            // Create model elements using the UI thread by using  
            // the Invoke method on the progress form. Always   
            // modify the model and diagrams from a UI thread.  
            form.Invoke((MethodInvoker)(delegate  
            {  
              IClass newClass = store.Root.CreateClass();  
              newClass.Name = string.Format("NewClass{0}", i);  
              diagram.Display(newClass);  
            }));  
  
            // Sleep briefly so that we can watch the updates.  
            Thread.Sleep(500);  
          }  
  
          // Commit the transaction or it will be rolled back.  
          transaction.Commit();  
        }  
      };  
  
      // Close the form when the thread completes.  
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)  
      {  
        form.Close();  
      };  
  
      // Start the thread before showing the modal progress dialog.  
      worker.RunWorkerAsync();  
  
      // Show the form modally, parented on VS.  
      // Prevents the user from making changes while in progress.  
      form.ShowDialog();  
    }  
  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
  
    public string Text  
    {  
      get { return "Add several classes"; }  
    }  
  }  
}  
```  
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Как разрешить пользователю отменить поток из примера  
  
1. Добавьте кнопку отмены в диалоговое окно с индикатором хода выполнения.  
  
2. Добавьте в диалоговое окно приведенный ниже код.  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3. В метод Execute() после конструкции формы добавьте следующую строку:  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>Другие методы доступа к потоку пользовательского интерфейса  
 Если нет необходимости создавать диалоговое окно, можно получить доступ к элементу управления, который отображает схему.  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Для выполнения операций в потоке пользовательского интерфейса можно использовать метод `uiThreadHolder.Invoke()`.  
  
## <a name="see-also"></a>См. также  
 [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Определение обработчика жестов на схеме моделирования](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
