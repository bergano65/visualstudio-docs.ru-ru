---
title: "Интеграция моделей с помощью Visual Studio Modelbus | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 26
caps.handback.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Интеграция моделей с помощью Visual Studio Modelbus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus предоставляет метод для создания связей между моделями и из других средств в модели. Например можно связать модели доменного языка \(DSL\) и моделей UML. Можно создать интегрированный набор DSL.  
  
 ModelBus позволяет создать уникальную ссылку на модель или на определенный элемент внутри модели. В этом справочнике могут храниться вне модели, например, в элемент в другой модели. Если впоследствии, средство хочет получить доступ к элементу, инфраструктура Modelbus загрузит соответствующую модель и возвратить элемент. Если требуется, модель можно отобразить для пользователя. Если файл не может осуществляться в ее предыдущем местоположении, ModelBus предложит пользователю его найти. Если пользователь найдет файл, ModelBus исправит все ссылки на этот файл.  
  
> [!NOTE]
>  В текущем [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Реализация ModelBus связанные модели должны быть элементами того же [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения.  
  
 Дополнительные сведения и пример кода см.  
  
-   [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)  
  
-   [Пакет SDK моделирования для Visual Studio](http://www.microsoft.com/download/details.aspx?id=40754)  
  
##  <a name="provide"></a> Предоставление доступа к DSL  
 Перед созданием ссылок ModelBus на модель или ее элементы необходимо определить ModelBusAdapter для DSL. Для этого проще всего использовать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Расширение шины модели, который добавляет команды в конструктор DSL.  
  
###  <a name="expose"></a> Для предоставления определения доменного языка для шины модели  
  
1.  Загрузите и установите расширение шины модели Visual Studio, если оно уже установлено. Дополнительные сведения см. в разделе [визуализации и моделирования SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
2.  Откройте файл определения DSL. Щелкните правой кнопкой мыши область конструктора и выберите **Включить Modelbus**.  
  
3.  В диалоговом окне выберите **я хочу предоставить этот DSL для ModelBus**. Можно выбрать оба параметра, если требуется, чтобы этот DSL предоставил свои модели и использовать ссылки на другие DSL.  
  
4.  Нажмите кнопку **ОК**. Новый проект «ModelBusAdapter» добавляется в решение DSL.  
  
5.  Если требуется доступ к DSL из текстового шаблона, необходимо изменить файл AdapterManager.tt в новом проекте. Пропустите этот шаг, если требуется доступ к DSL из другого кода, например командами и обработчиками событий. Для получения дополнительной информации см. [Использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
    1.  Измените базовый класс adaptermanagerbase на класс <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.  
  
    2.  Ближе к концу файла вставьте этот дополнительный атрибут перед классом AdapterManager:  
  
         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`  
  
    3.  Добавьте в проект ссылки на ModelBusAdapter **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**.  
  
     Если вы хотите открыть DSL из текстовых шаблонов, а также из другого кода, необходимо два адаптера, один измененный и один неизмененный.  
  
6.  Щелкните **Преобразовать все шаблоны**.  
  
7.  Выполните повторную сборку решения.  
  
 Теперь Modelbus может открывать экземпляры этого DSL.  
  
 Папка `ModelBusAdapters\bin\*` содержит сборки, построенные `Dsl` проекта и `ModelBusAdapters` проекта. Чтобы сослаться на этот DSL из другого DSL, следует импортировать эти сборки.  
  
### Убедившись, что можно ссылаться на элементы  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus адаптеры используют идентификатор guid элемента для идентификации по умолчанию. Эти идентификаторы, поэтому должен быть сохранен в файле модели.  
  
##### Чтобы убедиться в сохранности идентификаторов  
  
1.  Откройте файл DslDefinition.dsl.  
  
2.  В обозревателе DSL разверните **поведение XML\-сериализации**, затем **данные класса**.  
  
3.  Для каждого класса, к которому вы хотите создать шины модели ссылается на:  
  
     Щелкните узел класса и в окне «Свойства» убедитесь, что **идентификатор сериализации** равен `true`.  
  
 Кроме того Если вы хотите использовать имена элементов для определения элементов, а не идентификаторов GUID, можно переопределить части созданных адаптеров. Переопределите следующие методы в класс адаптера:  
  
-   Переопределение `GetElementId` для возвращения идентификатора, который вы хотите использовать. Этот метод вызывается при создании ссылок.  
  
-   Переопределение `ResolveElementReference` найти правильный элемент из ссылки шины модели.  
  
##  <a name="editRef"></a> Доступ к DSL из другого DSL  
 Можно хранить ссылки Modelbus в свойстве домена в DSL, а можно написать пользовательский код, который использует их. Можно также позволить пользователю создавать ссылки Modelbus, выбирая файлы модели и элемент внутри него.  
  
 Чтобы позволить DSL использовать ссылки на другой DSL, необходимо сначала сделать его *потребителя* ссылок Modelbus.  
  
#### Чтобы позволить DSL использовать ссылки на предоставляемый DSL  
  
1.  В схеме определения DSL щелкните правой кнопкой мыши основную часть диаграммы и нажмите кнопку **Включить Modelbus**.  
  
2.  В диалоговом окне выберите **я хочу разрешить этой модели получать ссылки Modelbus**.  
  
3.  В проекте Dsl принимающего DSL добавьте ссылки проекта следующие сборки. Вы найдете эти сборки \(DLL\-файлы\) в каталоге ModelBusAdapter\\bin\\ \* предоставляемого DSL.  
  
    -   Сборка предоставляемого DSL, например **Fabrikam.FamilyTree.Dsl.dll**  
  
    -   Предоставляется модели шины сборке адаптера, например **Fabrikam.FamilyTree.ModelBusAdapter.dll**  
  
4.  Добавьте следующие сборки .NET в ссылки проекта много проекта DSL.  
  
    1.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
    2.  **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**  
  
#### Для хранения ссылки Modelbus в свойстве домена  
  
1.  В определении DSL принимающего DSL добавьте свойство домена класса домена и присвойте ему имя.  
  
2.  В окне свойств свойство домена установлен, установите **тип** для `ModelBusReference`.  
  
 На этом этапе программного кода можно задать значение свойства, но она доступна только для чтения в окне «Свойства».  
  
 Можно разрешить пользователям задавать свойства с помощью специализированного редактора ссылок ModelBus. Существуют две версии этого редактора или *выбора:* один разрешает пользователям выбирать файл модели, а другой разрешает пользователям выбирать файл модели и элемент внутри модели.  
  
#### Чтобы разрешить пользователю устанавливать ссылку Modelbus в свойстве домена  
  
1.  Щелкните правой кнопкой мыши свойство домена и нажмите кнопку **изменить некоторые свойства ModelBusReference**. Откроется диалоговое окно. Это *средство выбора Model Bus*.  
  
2.  Выберите соответствующий **Тип ModelBusReference**: в модель или элемент внутри модели.  
  
3.  В строке фильтра диалогового окна файла введите строку, такие как `Family Tree files |*.ftree`. Замените расширение файла предоставляемого DSL.  
  
4.  Если выбрана ссылка на элемент в модели, можно добавить список типов, которые пользователь может выбрать, например Company.FamilyTree.Person.  
  
5.  Щелкните **ОК**, а затем нажмите кнопку **Преобразовать все шаблоны** на панели инструментов обозревателя решений.  
  
    > [!WARNING]
    >  Если вы не выбрали допустимая модель или сущность, кнопку «OK» не будет действовать, хотя может показаться включен.  
  
6.  Если указан список целевых типов, таких как Company.FamilyTree.Person, затем необходимо добавить ссылку на сборку в проект DSL, ссылающуюся на DLL целевого DSL, например Company.FamilyTree.Dsl.dll  
  
#### Для проверки ссылки Modelbus  
  
1.  Постройте предоставляемый и принимающий DSL.  
  
2.  Запустите один из DSL в экспериментальном режиме, нажав клавишу F5 или CTRL \+ F5.  
  
3.  Отладка проекта в экспериментальном экземпляре [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], добавьте файлы, являющиеся экземплярами каждого DSL.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus может разрешать ссылки только для моделей, которые являются элементами того же [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения. Например нельзя создать ссылку на файл модели в другой части файловой системы.  
  
4.  Создать несколько элементов и связей в экземпляре предоставляемого DSL и сохраните его.  
  
5.  Откройте экземпляр принимающего DSL и выберите элемент модели, имеющий свойство ссылки Modelbus.  
  
6.  В окне "Свойства" дважды щелкните свойство ссылки Modelbus. Откроется диалоговое окно выбора.  
  
7.  Щелкните **Обзор** и выберите экземпляр предоставляемого DSL.  
  
     Средство выбора также позволяет выбрать элемент в модели, при указании конкретного элемента тип ссылки Modelbus.  
  
## Создание ссылок в программном коде  
 Если вы хотите сохранить ссылку на модель или элемент внутри модели, создание `ModelBusReference`. Существует два типа из `ModelBusReference`: ссылки на модель и ссылки на элемент.  
  
 Чтобы создать ссылку на модель, требуется AdapterManager доменного модели которого является экземпляром и имя файла или [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] элемент проекта модели.  
  
 Чтобы создать ссылку на элемент, адаптер требуется для файла модели и элемент, который требуется для ссылки.  
  
> [!NOTE]
>  С [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus, можно создавать ссылки только на элементы в том же [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решения.  
  
### Импорт предоставляемых сборок DSL  
 В принимающем проекте добавьте ссылки на сборки DSL и ModelBusAdapter предоставляемого DSL.  
  
 Например предположим, что вы хотите сохранить ссылки ModelBus в элементах DSL библиотеки MusicLibrary. Ссылки ModelBus будут ссылаться на элементы FamilyTree DSL. В `Dsl` решения MusicLibrary и в узле ссылок проекта, добавьте ссылки на следующие сборки:  
  
-   Fabrikam.FamilyTree.Dsl.dll — предоставляемый DSL.  
  
-   Fabrikam.FamilyTree.ModelBusAdapters.dll — адаптер ModelBus предоставляемого DSL.  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
-   Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0  
  
 Эти сборки можно найти в `ModelBusAdapters` проекта, предоставляемого DSL в разделе `bin\*`.  
  
 В файле кода, в которой будет создаваться ссылки обычно нужно импортировать эти пространства имен:  
  
```  
// The namespace of the DSL you want to reference:  
using Fabrikam.FamilyTree;  // Exposed DSL  
using Fabrikam.FamilyTree.ModelBusAdapters;  
using Microsoft.VisualStudio.Modeling.Integration;  
using System.Linq;  
...  
```  
  
### Чтобы создать ссылку на модель  
 Чтобы создать ссылку на модель, доступ к AdapterManager для предоставляемого DSL и использовать его для создания ссылки на модель. Можно указать либо путь к файлу, или `EnvDTE.ProjectItem`.  
  
 Из AdapterManager можно получить адаптер, который предоставляет доступ к отдельным элементам в модели.  
  
> [!NOTE]
>  Адаптер необходимо уничтожить, когда закончите с ним. Наиболее удобный способ добиться этого — с `using` инструкции. Это показано в следующем примере.  
  
```  
// The file path of a model instance of the FamilyTree DSL:  
string targetModelFile = "TudorFamilyTree.ftree";  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Get an adapterManager for the target DSL:  
FamilyTreeAdapterManager manager =   
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)   
     as FamilyTreeAdapterManager;  
// or: (modelBus.FindAdapterManagers(targetModelFile).First())  
// or could provide an EnvDTE.ProjectItem  
  
// Create a reference to the target model:  
// NOTE: the target model must be a file in this project.  
ModelBusReference modelReference =  
     manager.CreateReference(targetModelFile);  
// or can use an EnvDTE.ProjectItem instead of the filename  
  
// Get the root element of this model:  
using (FamilyTreeAdapter adapter =   
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)  
{  
  FamilyTree modelRoot = adapter.ModelRoot;  
  // Access elements under the root in the usual way:  
  foreach (Person p in modelRoot.Persons) {...}  
  // You can create adapters for individual elements:  
  ModelBusReference elementReference =  
     adapter.GetElementReference(person);  
  ...  
} // Dispose adapter  
  
```  
  
 Если вы хотите иметь возможность использовать `modelReference` позднее, ее можно сохранить в свойстве домена, который имеет внешний тип `ModelBusReference`:  
  
```  
using Transaction t = this.Store.TransactionManager  
    .BeginTransaction("keep reference"))  
{  
  artist.FamilyTreeReference = modelReference;  
  t.Commit();  
}  
```  
  
 Чтобы разрешить пользователям изменять свойство домена, используйте `ModelReferenceEditor` как параметр в атрибуте Editor. Дополнительные сведения см. в разделе [Разрешить пользователю редактировать ссылку](#editRef).  
  
### Чтобы создать ссылку на элемент  
 Адаптер, который вы создали для модели можно использовать для создания и разрешения ссылок.  
  
```  
// person is an element in the FamilyTree model:  
ModelBusReference personReference =   
  adapter.GetElementReference(person);  
```  
  
 Если вы хотите иметь возможность использовать `elementReference` позднее, ее можно сохранить в свойстве домена, который имеет внешний тип `ModelBusReference`. Чтобы предоставить пользователям возможность изменить его, используйте `ModelElementReferenceEditor` как параметр в атрибуте Editor. Дополнительные сведения см. в разделе [Разрешить пользователю редактировать ссылку](#editRef).  
  
### Разрешение ссылок  
 Если у вас есть `ModelBusReference` \(MBR\) можно получить модель или элемент модели, к которому он относится. Если элемент представлен на схеме или в другом представлении, можно открыть представление и выберите элемент.  
  
 Из MBR можно создать адаптер. Из адаптера можно получить корень модели. Также можно разрешить MBR, ссылающиеся на конкретные элементы внутри модели.  
  
```  
using Microsoft.VisualStudio.Modeling.Integration; ...  
ModelBusReference elementReference = ...;  
  
// Get the ModelBus service:  
IModelBus modelBus =   
    this.Store.GetService(typeof(SModelBus)) as IModelBus;  
// Use a model reference or an element reference  
// to obtain an adapter for the target model:  
using (FamilyTreeAdapter adapter =   
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)  
   // or CreateAdapter(modelReference)  
{  
  // Get the root of the model:  
  FamilyTree tree = adapter.ModelRoot;  
  
  // Get a model element:  
  MyDomainClass mel =  
    adapter.ResolveElementReference<MyDomainClass>(elementReference);  
  if (mel != null) {...}  
  
  // Get the diagram or other view, if there is one:  
  ModelBusView view = adapter.GetDefaultView();  
  if (view != null)   
  {  
   view.Open();  
   // Display the diagram:  
   view.Show();   
   // Attempt to select the shape that presents the element:  
   view.SetSelection(elementReference);  
  }  
} // Dispose the adapter.  
```  
  
##### Разрешение ссылок ModelBus в текстовом шаблоне  
  
1.  DSL, к которому необходимо получить доступ к должен быть установлен адаптер ModelBus, который был настроен для доступа с помощью текстовых шаблонов. Для получения дополнительной информации см. [Предоставление доступа к DSL](#provide).  
  
2.  Как правило можно будет обращаться к целевому DSL осуществляется с помощью ссылки шины модели \(MBR\) хранится в исходном DSL. Таким образом, шаблон включает директиву исходного DSL и код для разрешения MBR. Дополнительные сведения о текстовых шаблонах см. в разделе [Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md).  
  
    ```  
    <#@ template debug="true" hostspecific="true"   
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>   
    <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>  
    <#@ output extension=".txt" #>  
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>  
    <#@ assembly name = "System.Core" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>  
    <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>  
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="Company.CompartmentDragDrop" #>  
    <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>  
    <# // Get source root from directive processor:  
      ExampleModel source = this.ExampleModel;   
      // This DSL has a MBR in its root:  
    using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)   
      {  
      ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();  
      ModelBusReference modelReference =  
        manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));  
  
      // Get the root element of this model:  
      using (CompartmentDragDropAdapter adapter =   
         this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)  
      {  
        ModelRoot root = adapter.ModelRoot;  
    #>  
    [[<#= root.Name #>]]  
    <#  
      }  
    #>  
  
    ```  
  
 Дополнительные сведения и пошаговое руководство см. [Использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md)  
  
## Сериализация для ModelBusReference  
 Если вы хотите сохранить `ModelBusReference` \(MBR\) в виде строки, ее можно сериализовать:  
  
```  
string serialized = modelBus.SerializeReference(elementReference);  
// Store it anywhere, then get it back again:  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, null);  
```  
  
 MBR, сериализованная подобным образом не зависит от контекста. При использовании простой файл\-адаптера Modelbus MBR содержит абсолютный путь к файлу. Этого достаточно, если файлы модели экземпляра никогда не перемещаются. Тем не менее, файлы модели обычно являются элементами в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта. Пользователи будут хотят иметь возможность перемещать весь проект в различные части файловой системы. Они также ожидать сможет сохранить проект в системе управления версиями и открыть его на разных компьютерах. Поэтому имена путей сериализовано относительно расположения проекта, который содержит файлы.  
  
### Сериализация относительно указанного пути файла  
 Объект `ModelBusReference` содержит `ReferenceContext`, который представляет собой словарь, в котором можно хранить сведения, такие как путь к файлу, относительно которого они должны быть сериализованы.  
  
 Сериализация относительно пути:  
  
```  
elementReference.ReferenceContext.Add(  
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,   
   currentProjectFilePath);  
string serialized = modelBus.SerializeReference(elementReference);  
```  
  
 Для получения ссылок на строки:  
  
```  
ReferenceContext context = new ReferenceContext();  
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,  
    currentProjectFilePath);  
ModelBusReference elementReferenceRestored =  
    modelBus.DeserializeReference(serialized, context);  
```  
  
### Ссылки Modelbus, созданные другими адаптерами  
 Следующие сведения являются полезным, если требуется создать собственный адаптер.  
  
 A `ModelBusReference` \(MBR\) состоит из двух частей: заголовка MBR, который десериализуется шины модели, и конкретного адаптера, обрабатываемый специальным диспетчером адаптеров. Это позволяет обеспечить собственный формат сериализации адаптера. Например можно было ссылаться в базе данных, а не файл, или Дополнительные сведения можно хранить в ссылке на адаптер. Собственный адаптер может помещать дополнительные сведения в `ReferenceContext`.  
  
 При десериализации MBR необходимо предоставить ReferenceContext, который сохраняется в объекте MBR. При сериализации MBR, сохраненное значение ReferenceContext используется адаптером для создания строки. Десериализованный строка не содержит все данные, указанные в ReferenceContext. Например в простой файловый адаптер, ReferenceContext содержит корневой путь к файлу, который не хранится в сериализованной строке MBR.  
  
 MBR десериализуется в два этапа:  
  
-   `ModelBusReferencePropertySerializer` представляет собой стандартный сериализатор, который работает с заголовком MBR. Он использует стандартный для DSL `SerializationContext` контейнер свойств, который хранится в `ReferenceContext` с помощью ключа `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`. В частности `SerializationContext` должен содержать экземпляр `ModelBus`.  
  
-   Адаптер ModelBus работает с адаптерной частью MBR. Он может использовать дополнительные сведения, сохраненные в ReferenceContext MBR. Простой файловый адаптер хранит корневые пути к файлу с помощью клавиш `FilePathLoadContextKey` и `FilePathSaveContextKey`.  
  
     Ссылка на адаптер в файле модели десериализуется только в том случае, если он используется.  
  
## Создание модели  
  
### Создание, открытие и изменение модели  
 Следующий фрагмент взят из пример конечного автомата на сайте VMSDK. Демонстрирует использование ссылок Modelbus для создания и открытия модели и схема, связанные с моделью.  
  
 В этом примере целевой DSL называется StateMachine. Несколько имен являются производными от него, например имя класса модели и имя ModelBusAdapter.  
  
```  
using Fabrikam.StateMachine.ModelBusAdapters;   
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Integration;  
using Microsoft.VisualStudio.Modeling.Integration.Shell;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
// Create a new model.  
ModelBusReference modelReference =   
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);  
//Keep reference of new model in this model.  
using (Transaction t = ...)  
{  
  myModelElement.ReferenceProperty = modelReference;  
  t.Commit();  
}  
// Get the ModelBus service from Visual Studio.  
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.  
    GetGlobalService(typeof(SModelBus)) as IModelBus;  
// Get a modelbus adapter on the new model.  
ModelBusAdapter modelBusAdapter;  
modelBus.TryCreateAdapter(modelReference,   
    this.ServiceProvider, out modelBusAdapter);  
using (StateMachineAdapter adapter =   
      modelBusAdapter as StateMachineAdapter)  
{  
    if (adapter != null)  
    {  
        // Obtain a Diagram from the adapter.  
        Diagram targetDiagram =   
           ((StandardVsModelingDiagramView)  
                 adapter.GetDefaultView()  
            ).Diagram;  
  
        using (Transaction t =   
             targetDiagram.Store.TransactionManager  
                .BeginTransaction("Update diagram"))  
        {  
            DoUpdates(targetDiagram);  
            t.Commit();  
        }  
  
        // Display the new diagram.  
        adapter.GetDefaultView().Show();  
    }  
}  
```  
  
## Проверка ссылок  
 BrokenReferenceDetector проверяет все свойства домена в хранилище, которое может содержать ссылки Modelbus. Он вызывает действие, укажите, где найти какие\-либо действия. Это особенно полезно для методов проверки. Следующий метод проверки тестирует хранилище, пытаясь сохранить модель и сообщает неработающие ссылки в окне ошибок:  
  
```  
[ValidationMethod(ValidationCategories.Save)]  
public void ValidateModelBusReferences(ValidationContext context)  
{  
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,  
    delegate(ModelElement element, // parent of property  
             DomainPropertyInfo property, // identifies property  
             ModelBusReference reference) // invalid reference  
    {   
      context.LogError(string.Format(INVALID_REF_FORMAT,   
             property.Name,   
             referenceState.Name,   
             new ModelBusReferenceTypeConverter().  
                 ConvertToInvariantString(reference)),   
         "Reference",   
         element);  
      });  
}}  
private const string INVALID_REF_FORMAT =   
    "The '{0}' domain property of ths ReferenceState instance "  
  + "named '{1}' contains reference value '{2}' which is invalid";  
```  
  
## Действия, выполняемые расширением ModelBus  
 Следующие сведения не очень важен, но может пригодиться при широком использовании ModelBus.  
  
 Расширение ModelBus вносит следующие изменения в решение DSL.  
  
 При щелчке правой кнопкой мыши схему определения DSL, щелкните **Включить Modelbus**, а затем выберите **включить этот DSL использовать ModelBus**:  
  
-   В проекте DSL ссылка добавляется **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**  
  
-   В определении DSL добавляется ссылка внешнего типа: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.  
  
     Можно увидеть ссылки в **Обозреватель DSL**, в разделе **типов домена**. Чтобы добавить ссылки внешнего типа вручную, щелкните правой кнопкой мыши корневой узел.  
  
-   Добавлен новый файл шаблона, **Dsl\\GeneratedCode\\ModelBusReferencesSerialization.tt**.  
  
 Если вы установите тип свойства домена для ModelBusReference, щелкните правой кнопкой мыши свойство и нажмите кнопку **Включить специальные свойства ModelBusReference**:  
  
-   Свойство domain добавляются несколько атрибутов среды CLR. Их можно увидеть в поле пользовательские атрибуты в окне «Свойства». В **Dsl\\GeneratedCode\\DomainClasses.cs**, можно просмотреть атрибуты в объявлении свойства:  
  
    ```  
    [System.ComponentModel.TypeConverter(typeof(  
    Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]  
    [System.ComponentModel.Editor(typeof(  
      Microsoft.VisualStudio.Modeling.Integration.Picker  
      .ModelReferenceEditor // or ModelElementReferenceEditor  
      ), typeof(System.Drawing.Design.UITypeEditor))]  
    [Microsoft.VisualStudio.Modeling.Integration.Picker  
      .SupplyFileBasedBrowserConfiguration  
      ("Choose a model file", "Target model|*.target")]  
    ```  
  
 При щелчке правой кнопкой мыши схему определения DSL, нажмите кнопку **Включить ModelBus**, и выберите **предоставить этот DSL для ModelBus**:  
  
-   Новый проект `ModelBusAdapter` добавляется в решение.  
  
-   Ссылку на `ModelBusAdapter` добавляется `DslPackage` проекта.`ModelBusAdapter` содержит ссылку на `Dsl` проекта.  
  
-   В **DslPackage\\source.extention.tt**, `|ModelBusAdapter|` добавляется в качестве компонента MEF.  
  
## См. также  
 [Практическое руководство. Открытие модели из файла в коде программы](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Интеграция моделей UML с другими моделями и средствами](../modeling/integrate-uml-models-with-other-models-and-tools.md)   
 [Практическое руководство. Добавление обработчика перетаскивания](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Использование Visual Studio ModelBus в текстовом шаблоне](../modeling/using-visual-studio-modelbus-in-a-text-template.md)