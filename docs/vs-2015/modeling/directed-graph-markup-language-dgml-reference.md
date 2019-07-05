---
title: Справочник по языку разметки графов (DGML) направлены | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0de96057326a9e4b6a64865ef34972d5542aff30
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443001"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Справочник по языку DGML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Язык разметки направленных графов (Directed Graph Markup Language, DGML) описывает информацию, которая используется для визуализации и выполнения анализов сложности, а также служит форматом, в котором Visual Studio хранит карты кодов. Для описания циклических и ациклических направленных графов в DGML используется простой XML-код. Направленный граф представляет собой набор узлов, соединенных ссылками или границами. Узлы и ссылки могут быть использованы для представления сетевых структур, например элементов программного проекта.  
  
 Обратите внимание, что некоторые версии Visual Studio поддерживают только некоторые возможности DGML см. в разделе [поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
> При редактировании DGML-файла IntelliSense показывает атрибуты, доступные для данного элемента, и их значения. Задавая цвет с помощью атрибута, можно использовать имена для обычных цветов, например "Blue", или шестнадцатеричные значения ARGB, например "#ffa0b1c3". DGML использует небольшое подмножество форматов определения цветов Windows Presentation Foundation (WPF). Дополнительные сведения см. в разделе [цвета классе](http://go.microsoft.com/fwlink/?LinkId=182345).  
  
## <a name="DGML"></a> Синтаксис DGML  
 В следующей таблице описаны виды элементов, используемых в языке DGML.  
  
- `<DirectedGraph></DirectedGraph>`  
  
   Это корневой элемент документа с картой кода (.dgml). Все остальные DGML-элементы отображаются внутри области этого элемента.  
  
   Следующий список описывает необязательные атрибуты, которые могут быть включены в элемент.  
  
   `Background` — цвет фона.  
  
   `BackgroundImage` — местоположение файла изображения, используемого в качестве фона карты.  
  
   `GraphDirection` — если для карты выбрана древовидная структура (`Sugiyama`), расположите узлы таким образом, чтобы большинство ссылок было упорядочены в определенном направлении: `TopToBottom`, `BottomToTop`, `LeftToRight` или `RightToLeft`. См. в разделе [изменение макета карты](../modeling/browse-and-rearrange-code-maps.md#Selecting).  
  
   `Layout` — организует карту в одну из следующих структур: `None`, `Sugiyama` (древовидная структура), `ForceDirected` (быстрые кластеры) или `DependencyMatrix`. См. в разделе [изменение макета карты](../modeling/browse-and-rearrange-code-maps.md#Selecting).  
  
   `NeighborhoodDistance` — если карта организована в виде древовидной структуры или быстрых кластеров, показывает только узлы, удаленные от выбранных узлов не более, чем на указанное количество ссылок (1–7). См. в разделе [изменение макета карты](../modeling/browse-and-rearrange-code-maps.md#Selecting).  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Nodes>  
        ...  
     </Nodes>  
     <Links>  
        ...  
     </Links>  
     <Categories>  
        ...  
     </Categories>  
     <Properties>  
        ...  
     </Properties>  
  </DirectedGraph>  
  ```  
  
- `<Nodes></Nodes>`  
  
   Необязательный элемент содержит список элементов `<Node/>`, задающих узлы карты. Дополнительные сведения см. в описании элемента `<Node/>`.  
  
  > [!NOTE]
  > Если сослаться в элементе `<Link/>` на несуществующий элемент карты, она создаст элемент `<Node/>` автоматически.  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Nodes>  
        <Node ... />  
     </Nodes>  
     <Links>  
        <Link ... />  
     </Links>  
  </DirectedGraph>  
  ```  
  
- `<Node/>`  
  
   Этот элемент определяет единичный узел. Он отображается внутри списка элементов `<Nodes><Nodes/>`.  
  
   Этот элемент в обязательном порядке включает следующие атрибуты.  
  
   `Id` — уникальное имя узла; одновременно является значением по умолчанию атрибута `Label`, если атрибут `Label` не определен отдельно. Это имя должно совпадать с атрибутом `Source` или `Target` ссылки, которая ссылается на данный элемент.  
  
   Следующий список описывает некоторые из необязательных атрибутов, которые могут быть включены в элемент.  
  
   `Label` — Отображаемое имя узла.  
  
   Атрибуты стилей. См. раздел [Настройка карт кода путем редактирования DGML-файлов](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   `Category` — имя категории, которая указывает на элементы, имеющие одинаковое значение этого атрибута. Дополнительные сведения см. в описании элемента `<Category/>`.  
  
   `Property` — имя свойства, указывающего на элементы, которые имеют одинаковое значение этого свойства. Дополнительные сведения см. в описании элемента `<Property/>`.  
  
   `Group` — если узел содержит другие узлы, следует присвоить этому атрибуту значение `Expanded` или `Collapsed`, чтобы его содержимое отображалось или скрывалось. Обязателен элемент `<Link/>`, включающий атрибут `Category="Contains"` и задающий родительский узел как исходный узел и дочерние узлы как целевые. См. в разделе [группирования элементов кода](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).  
  
   `Visibility` — следует задать этому атрибуту значение `Visible`, `Hidden` или `Collapsed`. Используются сочетания клавиш `System.Windows.Visibility`. См. в разделе [скрытие и отображение узлов и ссылок](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).  
  
   `Reference` — задайте этот атрибут для связывания с документом или URL-адресом. См. в разделе [связать документы или URL-адреса с кодовым точкам и связям](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Nodes>  
        <Node Id="Driver" Label="Student" Category="Person" />  
        <Node Id="Passenger" Label="Instructor" Category="Person" />  
        <Node Id="Car" Label="Car" Category="Automobile" />  
        <Node Id="Truck" Label="Truck" Category="Automobile" />  
     </Nodes>  
     <Links>  
        <Link ... />  
     </Links>  
     <Categories>  
        <Category Id="Person" Background="Orange" />  
        <Category Id="Automobile" Background="Yellow"/>  
     </Categories>  
  </DirectedGraph>  
  ```  
  
- `<Links></Links>`  
  
   Этот элемент содержит список элементов `<Link>`, задающих ссылки между узлами. Дополнительные сведения см. в описании элемента `<Link/>`.  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Links>  
        <Link ... />  
     </Links>  
  </DirectedGraph>  
  ```  
  
- `<Link/>`  
  
   Этот элемент определяет единичную ссылку, соединяющую исходный узел с целевым узлом. Он отображается внутри списка элементов `<Links></Links>`.  
  
  > [!NOTE]
  > Если данный элемент ссылается на неопределенный узел, документ карты автоматически создаст узел с заданными атрибутами, если таковые имеются.  
  
   Этот элемент в обязательном порядке включает следующие атрибуты.  
  
   `Source` — исходный узел ссылки.  
  
   `Target` — целевой узел ссылки.  
  
   Следующий список описывает некоторые из необязательных атрибутов, которые могут быть включены в элемент.  
  
   `Label` — отображаемое имя ссылки.  
  
   Атрибуты стилей. См. раздел [Настройка карт кода путем редактирования DGML-файлов](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   `Category` — имя категории, которая указывает на элементы, имеющие одинаковое значение этого атрибута. Дополнительные сведения см. в описании элемента `<Category/>`.  
  
   `Property` — имя свойства, указывающего на элементы, которые имеют одинаковое значение этого свойства. Дополнительные сведения см. в описании элемента `<Property/>`.  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Nodes>  
        <Node Id="Driver" Label="Student" Category="Person" />  
        <Node Id="Passenger" Label="Instructor" Category="Person" />  
        <Node Id="Car" Label="Car" Category="Automobile" />  
        <Node Id="Truck" Label="Truck" Category="Automobile" />  
     </Nodes>  
     <Links>  
        <Category Id="Person" Background="Orange" />  
        <Category Id="Automobile" Background="Yellow"/>  
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />  
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />  
     </Links>  
  </DirectedGraph>  
  ```  
  
- `<Categories></Categories>`  
  
   Этот элемент содержит список элементов `<Category/>`. Дополнительные сведения см. в описании элемента `<Category/>`.  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Categories>  
         <Category ... />  
     </Categories>  
  </DirectedGraph>  
  ```  
  
- `<Category/>`  
  
   Этот элемент определяет атрибут `Category`, который используется для указания на элементы, имеющие одинаковые значения этого атрибута. Атрибут `Category` может использоваться для упорядочивания элементов карты, для предоставления общих атрибутов через наследование или для определения дополнительных метаданных.  
  
   Этот элемент в обязательном порядке включает следующие атрибуты.  
  
   `Id` — уникальное имя категории; одновременно является значением по умолчанию атрибута `Label`, если атрибут `Label` не определен отдельно.  
  
   Следующий список описывает некоторые из необязательных атрибутов, которые могут быть включены в элемент.  
  
   `Label` — удобное для чтения имя категории.  
  
   `BasedOn` — родительская категория, от которой унаследован данный элемент `<Category/>`.  
  
   В примере категория `FailedTest` унаследовала атрибут `Stroke` от категории `PassedTest`. См. в подразделе «Создание иерархических категорий» в [Настройка карт кода путем редактирования DGML-файлов](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   Категории предоставляют также базовый шаблон поведения, который определяет отображение узлов и ссылок на карте. См. раздел [Настройка карт кода путем редактирования DGML-файлов](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Nodes>  
        <Node Id="Driver" Label="Driver" Category="Person" />  
        <Node Id="Car" Label="Car" Category="Automobile" />  
        <Node Id="Truck" Label="Truck" Category="Automobile" />  
        <Node Id="Passenger" Category="Person" />  
     </Nodes>  
     <Links>  
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />  
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />  
     </Links>  
     <Categories>  
        <Category Id="Person" Background="Orange" />  
        <Category Id="Automobile" Background="Yellow"/>  
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />  
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />  
     </Categories>  
  </DirectedGraph>  
  ```  
  
- `<Properties></Properties>`  
  
   Этот элемент содержит список элементов `<Property/>`. Дополнительные сведения см. в описании элемента `<Property/>`.  
  
   Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Properties>  
         <Property ... />  
     </Properties>  
  </DirectedGraph>  
  ```  
  
- `<Property/>`  
  
   Этот элемент определяет атрибут `Property`, который можно использовать для присваивания значения любому элементу или атрибуту DGML, включая категории и другие свойства.  
  
   Этот элемент в обязательном порядке включает следующие атрибуты.  
  
  - `Id` — уникальное имя свойства; одновременно является значением по умолчанию атрибута `Label`, если атрибут `Label` не определен отдельно.  
  
  - `DataType` — тип данных, хранящихся в свойстве.  
  
    Если требуется, чтобы свойство отображалось в **свойства** окно, используйте `Label` свойство, чтобы указать отображаемое имя свойства.  
  
    См. в разделе [Присвоение категорий кодовым точкам и связям](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).  
  
    Пример  
  
  ```xml  
  <?xml version="1.0" encoding="utf-8"?>  
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">  
     <Nodes>  
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>  
        <Node Id="Car" Label="Car" Category="Automobile" />  
        <Node Id="Truck" Label="Truck" Category="Automobile" />  
        <Node Id="Passenger" Category="Person" />  
     </Nodes>  
     <Links>  
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />  
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />  
     </Links>  
     <Categories>  
        <Category Id="Person" Background="Orange" />  
        <Category Id="Automobile" Background="Yellow"/>  
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />  
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />  
     </Categories>  
     <Properties>  
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />  
     </Properties>  
  </DirectedGraph>  
  ```  
  
### <a name="AddAlias"></a> Псевдонимы для часто используемых путей  
 Замена часто используемых путей псевдонимами уменьшает размер DGML-файла и время, требуемое на загрузку или сохранение файла. Для создания псевдонима добавьте раздел `<Paths></Paths>` в конце DGML-файла. В этом разделе добавьте элемент `<Path/>` для того, чтобы определить псевдоним для пути.  
  
```xml  
<Paths>  
   <Path Id="MyPathAlias" Value="C:\...\..." />  
</Paths>  
```  
  
 Чтобы сослаться на псевдоним из элемента DGML-файла, нужно вложить `Id` из \<путь / > символом доллара ($) и круглыми скобками (()):  
  
```xml  
<Nodes>  
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />  
</Nodes>  
<Properties>  
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />  
</Properties>  
```  
  
## <a name="see-also"></a>См. также  
 [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)   
 [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)
