---
title: Определение обработчика связей рабочего элемента | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 25143390085ec0b4d7ab56e0fef9920d7d5eceb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914554"
---
# <a name="define-a-work-item-link-handler"></a>Определение обработчика связей рабочего элемента
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Разработчик может создать расширение интеграции Visual Studio, реагирующее на создание или удаление пользователем связи между элементом модели UML и рабочим элементом. Например, если пользователь решит связать новый рабочий элемент с элементом модели, код расширения может заполнить поля рабочего элемента значениями, полученными из модели.  
  
## <a name="set-up-a-uml-extension-solution"></a>Настройка решения расширения UML  
 Позволяет разрабатывать обработчики и распространять их среди других пользователей. Необходимо настроить два проекта Visual Studio:  
  
-   Проект библиотеки классов, содержащий код обработчика ссылок.  
  
-   Проект VSIX, который выступает в роли контейнера для установки команды. При необходимости в проект VSIX можно добавить и другие компоненты.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>Настройка решения в Visual Studio  
  
1.  Создайте проект библиотеки классов, добавив его в существующее решение VSIX или создав новое решение.  
  
    1.  В меню **Файл** последовательно выберите пункты **Создать**и **Проект**.  
  
    2.  В разделе **установленные шаблоны**, разверните **Visual C#** или **Visual Basic**, выберите в среднем столбце **библиотеки классов**.  
  
    3.  В поле **Решение** укажите, нужно ли создать новое решение или добавить компонент в уже открытое решение VSIX.  
  
    4.  Укажите имя и расположение проекта и нажмите кнопку «ОК».  
  
2.  Создайте проект VSIX, если ваше решение еще его не содержит.  
  
    1.  В в контекстном меню решения в **обозревателе решений**выберите пункт **Добавить**, а затем **Новый проект**.  
  
    2.  В разделе **Установленные шаблоны**разверните узел **Visual C#** или **Visual Basic**и выберите пункт **Расширение среды**. В среднем столбце выберите пункт **Проект VSIX**.  
  
3.  Назначьте проект VSIX запускаемым проектом решения.  
  
    -   В контекстном меню проекта VSIX в обозревателе решений выберите пункт **Назначить запускаемым проектом**.  
  
4.  В **source.extension.vsixmanifest**в разделе **содержимого**, добавьте проект библиотеки классов в качестве компонента MEF.  
  
    1.  На вкладке **Метаданные** введите имя для VSIX.  
  
    2.  На вкладке **Цели установки** задайте в качестве целевых объектов версии Visual Studio.  
  
    3.  На вкладке **Активы** выберите **Создать**и укажите в диалоговом окне следующие значения:  
  
         **Тип** = **Компонент MEF**  
  
         **Источник** = **Проект в текущем решении**  
  
         **Проект** = *Ваш проект библиотеки классов*  
  
## <a name="defining-the-work-item-link-handler"></a>Определение обработчика ссылок рабочего элемента  
 Выполните все указанные ниже задачи в проекте библиотеки классов.  
  
### <a name="project-references"></a>Ссылки проекта  
 Добавьте в ссылки проекта следующие сборки [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]:  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -используется в примере кода  
  
 Если не удается найти одну из этих ссылок в разделе **.Net** вкладке **добавить ссылку** диалоговое окно, найти его в Visual Studio [версия] \Common7\IDE\ \Program Files\Microsoft вкладка обзора PrivateAssemblies\\.  
  
### <a name="import-the-work-item-namespace"></a>Импорт пространства имен рабочего элемента  
 В вашей [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта **ссылки**, добавьте ссылки на следующие сборки:  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  Импортируйте следующие пространства имен в коде программы:  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>Определение обработчика событий связанного рабочего элемента  
 Добавьте файл класса в проект библиотеки классов и задайте его содержимое указанным ниже образом. Измените пространство имен и имена классов в соответствии со своими предпочтениями.  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
  
namespace WorkItems  
{  
  [Export(typeof(ILinkedWorkItemExtension))]  
  public class MyWorkItemExtension : ILinkedWorkItemExtension  
  {  
    // Called before a new work item is edited by the user.  
    // Use this to initialize work item fields from the model element.  
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)  
    {  
      INamedElement namedElement =  
            elementsToBeLinked.First() as INamedElement;  
      if (namedElement != null)  
        workItemDocument.Item.Title = namedElement.Name;  
  
    }  
  
    // Called when any work item is linked to a model element.  
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)  
    {  
      foreach (IElement element in elements)  
        foreach (IShape shape in element.Shapes())  
          shape.Color = System.Drawing.Color.Red;  
    }  
  
    // Called when a work item is unlinked from a model element.  
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)  
    {  
      foreach (IShape shape in element.Shapes())  
        shape.Color = System.Drawing.Color.White;  
    }  
  }  
}  
```  
  
## <a name="testing-the-link-handler"></a>Тестирование обработчика ссылок  
 В целях проверки запустите обработчик ссылок в режиме отладки.  
  
> [!WARNING]
>  Вы должны быть уже подключены к управлению исходным кодом (SCC) TFS для создания рабочего элемента или связи с ним. При попытке открыть соединение с другим SCC TFS Visual Studio автоматически закрывает текущее решение. Убедитесь, что вы уже подключены соответствующему SCC, перед попыткой создания рабочего элемента или связи с ним. В последних выпусках Visual Studio команды меню недоступны, если вы не подключены к SCC.  
  
#### <a name="to-test-the-link-handler"></a>Проверка обработчика ссылок  
  
1.  Нажмите клавишу **F5**или выберите команду **Начать отладку** в меню **Отладка**.  
  
     Запустится экспериментальный экземпляр [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     **Устранение неполадок**: Если новый [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не запускается, убедитесь, что проект VSIX запускаемым проектом решения.  
  
2.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]откройте или создайте проект моделирования и откройте или создайте схему моделирования.  
  
3.  Создайте элемент модели (например, класс UML) и присвойте ему имя.  
  
4.  Щелкните правой кнопкой мыши элемент и нажмите кнопку **создать рабочий элемент**.  
  
    -   Если в подменю отображается **открыть подключение к Team Foundation Server**, необходимо будет закрыть проект, подключитесь к соответствующему TFS и перезапустить эту процедуру.  
  
    -   Если в подменю отображается список типов рабочих элементов, выберите один из них.  
  
         Откроется форма нового рабочего элемента.  
  
5.  Если вы воспользовались примером кода из предыдущего раздела, убедитесь, что название рабочего элемента совпадает с названием элемента модели. Это показывает, что метод `OnWorkItemCreated()` сработал.  
  
6.  Заполните форму, сохраните и закройте рабочий элемент.  
  
7.  Убедитесь, что рабочий элемент изменил цвет на красный. Это показывает работу метода `OnWorkItemLinked()` в примере кода.  
  
     **Устранение неполадок**: Если методы обработчика не запустились, убедитесь, что:  
  
    -   Проект библиотеки классов указан в качестве компонента MEF в **содержимого** в списке **source.extensions.manifest** проекта VSIX.  
  
    -   к классу обработчика присоединен верный атрибут `Export`, и этот класс реализует `ILinkedWorkItemExtension`;  
  
    -   параметры всех атрибутов `Import` и `Export` являются допустимыми.  
  
## <a name="about-the-work-item-handler-code"></a>Код обработчика рабочего элемента  
  
### <a name="listening-for-new-work-items"></a>Ожидание вызова при создании рабочих элементов  
 `OnWorkItemCreated` вызывается, если пользователь решает создать новый элемент, который необходимо связать с элементами модели. Код может инициализировать поля рабочего элемента. Затем рабочий элемент представляется пользователю, который может изменить значения полей и сохранить рабочий элемент. Ссылка на элемент модели не создается, пока рабочий элемент не будет успешно сохранен.  
  
```  
public void OnWorkItemCreated(  
    IEnumerable<IElement> elementsToBeLinked,  
    IWorkItemDocument workItem)  
{  
  INamedElement namedElement =   
         elementsToBeLinked.First() as INamedElement;  
  if (namedElement != null)  
      workItem.Item.Title = namedElement.Name;  
}  
```  
  
### <a name="listening-for-link-creation"></a>Ожидание вызова при создании ссылок  
 `OnWorkItemLinked` вызывается сразу после создания ссылки. Вызов производится независимо от того, на какой рабочий элемент указывает ссылка: новый или уже существующий, и осуществляется по одному разу для каждого рабочего элемента.  
  
```  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  foreach (IElement element in elements)  
    foreach (IShape shape in element.Shapes())  
         shape.Color = System.Drawing.Color.Red;  
}  
```  
  
> [!NOTE]
>  Чтобы этот пример работал, необходимо добавить ссылку на проект в `System.Drawing.dll` и импортировать пространство имен `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Для других реализаций `OnWorkItemLinked` эти дополнительные действия не требуются.  
  
### <a name="listening-for-link-removal"></a>Ожидание вызова при удалении ссылок  
 `OnWorkItemRemoved` вызывается один раз непосредственно перед удалением каждой связи рабочего элемента. При удалении элемента модели удаляются все связи.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Обновление рабочего элемента  
 С помощью пространств имен Team Foundation можно управлять рабочим элементом.  
  
 Чтобы воспользоваться следующим примером, добавьте в ссылки проекта следующие сборки .NET:  
  
-   Microsoft.TeamFoundation.Client.dll  
  
-   Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
```  
  
using Microsoft.TeamFoundation.Client;  
using Microsoft.TeamFoundation.WorkItemTracking.Client;  
...  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  TfsTeamProjectCollection tfs =  
        TfsTeamProjectCollectionFactory  
            .GetTeamProjectCollection(new Uri(serverUri));  
  WorkItemStore workItemStore = new WorkItemStore(tfs);  
  WorkItem item = workItemStore.GetWorkItem(workItemId);  
  item.Open();  
  item.Title = "something";  
  item.Save();  
}   
```  
  
## <a name="accessing-the-work-item-reference-links"></a>Доступ к ссылкам на рабочие элементы  
 Доступ к ссылкам можно получить следующим образом:  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Формат `linkString` выглядит следующим образом:  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 Здесь:  
  
- URL-адрес сервера будет следующим:  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   Регистр имеет значение в `projectCollection`.  
  
- `RepositoryGuid` можно получить через подключение к TFS.  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Дополнительные сведения о ссылках см. в разделе [элементам модели присоединение строк ссылок к UML](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Связывание элементов модели и рабочих элементов](../modeling/link-model-elements-and-work-items.md)   
 [Присоединение строк ссылок к элементам модели UML](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Определение и Установка расширения моделирования](../modeling/define-and-install-a-modeling-extension.md)   
 [Программирование с UML API](../modeling/programming-with-the-uml-api.md)



