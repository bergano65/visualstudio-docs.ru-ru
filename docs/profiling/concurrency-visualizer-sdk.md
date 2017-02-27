---
title: "Пакет SDK визуализатора параллелизма | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Пакет SDK визуализатора параллелизма
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно инструментировать свой исходный код с помощью пакета SDK визуализатора параллелизма для отображения дополнительных сведений в визуализаторе параллелизма.  Можно сопоставить дополнительные данные с этапами выполнения кода и событиями в коде.  Эти дополнительно отображаемые параметры известны как *маркеры*.  Ознакомительное пошаговое руководство см. в разделе [Introducing the Concurrency Visualizer SDK](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## Свойства  
 Флаги, диапазоны и сообщения имеют по 2 свойства: категория и важность.  В диалоговом окне [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) эти свойства можно использовать для фильтрации набора маркеров, которые отображаются.  Кроме того, эти свойства влияют на визуальное представление маркеров.  Например, размер флагов используется для представления важности.  Кроме того, цвет используется для краткого обозначения категории.  
  
## Основы использования  
 Визуализатор параллелизма по умолчанию предоставляет поставщика, который можно использовать для создания метки.  Поставщик уже зарегистрирован вместе с визуализатором параллелизма и нет необходимости в дополнительных действиях для того, чтобы маркеры отображались в пользовательском интерфейсе.  
  
### C\# и Visual Basic  
 В коде на языке C\#, Visual Basic или другом управляемом коде используйте поставщик по умолчанию путем вызова <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>.  Он предоставляет функции для создания маркеров: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> и <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>.  Для этих функций есть несколько перегруженных методов, в зависимости от того, нужно ли использовать значения по умолчанию для свойства.  Простейшая перегрузка принимает строковый параметр, который указывает только описание события.  Описание отображается в отчетах визуализатора параллелизма.  
  
##### Добавление поддержки SDK в C\# или проекты Visual Basic  
  
1.  В строке меню выберите **Анализировать**, **Визуализатор параллелизма**, **Добавить пакет SDK в проект**.  
  
2.  Выберите проект, в котором нужно получить доступ к пакету SDK, а затем нажмите кнопку **Добавить пакет SDK в выбранный проект**.  
  
3.  Добавьте к коду оператор imports или using.  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 В C\+\+ создайте объект [Класс marker\_series](../profiling/marker-series-class.md) и используйте его для вызова функций.  Класс `marker_series` предоставляет три функции для создания маркеров: [Метод marker\_series::write\_flag](../profiling/marker-series-write-flag-method.md), [Метод marker\_series::write\_message](../profiling/marker-series-write-message-method.md) и [Метод marker\_series::write\_alert](../profiling/marker-series-write-alert-method.md).  
  
##### Добавление поддержки SDK в проекты C\+\+ и C  
  
1.  В строке меню выберите **Анализировать**, **Визуализатор параллелизма**, **Добавить пакет SDK в проект**.  
  
2.  Выберите проект, в котором нужно получить доступ к пакету SDK, а затем нажмите кнопку **Добавить пакет SDK в выбранный проект**.  
  
3.  Для C\+\+, подключите библиотеку `cvmarkersobj.h`.  Для C, подключите библиотеку `cvmarkers.h`.  
  
4.  Добавьте к коду оператор using.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Создайте новый объект `marker_series` и передайте его конструктору `span`.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## Другие виды использования  
 Для сложных сценариев пакет SDK визуализатора параллелизма дополнительно предоставляет несколько элементов управления.  Два основных понятия сопоставлены с более сложными сценариями: поставщик маркеров и набор маркеров.  Поставщики маркеров представляют собой различные поставщики трассировки событий Windows \(каждый из которых имеет отличающийся от других GUID\).  Наборы маркеров представляют собой последовательные каналы событий, созданные одним поставщиком.  Их можно использовать для организации событий, созданных поставщиком маркеров.  
  
#### Использование нового поставщика маркеров в проектах на языке C\# или Visual Basic  
  
1.  Создайте объект <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Конструктор принимает идентификатор GUID.  
  
2.  Чтобы зарегистрировать поставщика, откройте диалоговое окно [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) визуализатора параллелизма.  Выберите вкладку **Маркеры**, а затем нажмите кнопку **Добавить нового поставщика**.  В диалоговом окне [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) введите идентификатор GUID, который использовался для создания поставщика, и описание поставщика.  
  
#### Использование нового поставщика маркеров в проектах на языке C\+\+ и C\#  
  
1.  Используйте функцию `CvInitProvider` для инициализации PCV\_PROVIDER.  Конструктор принимает GUID\* и PCV\_PROVIDER\*.  
  
2.  Чтобы зарегистрировать поставщика, откройте диалоговое окно [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Выберите вкладку **Маркеры**, а затем нажмите кнопку **Добавить нового поставщика**.  В этом диалоговом окне введите идентификатор GUID, который использовался для создания поставщика, и описание поставщика.  
  
#### Использование набора маркеров в проектах на языке C\# или Visual Basic  
  
1.  Для использования нового <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> сначала создайте его с помощью объекта <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>, а затем сформируйте события маркеров непосредственно из нового набора.  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### Чтобы использовать набор маркеров в проектах на C\+\+  
  
1.  Создайте объект `marker_series`.  События можно создавать из этого нового набора.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### Чтобы использовать набор маркеров в проектах на C  
  
1.  Используйте функцию `CvCreateMarkerSeries` для создания PCV\_MARKERSERIES.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## Связанные разделы  
  
|Название|Описание|  
|--------------|--------------|  
|[Справочник по библиотеке C\+\+](../profiling/cpp-library-reference.md)|Описывает API визуализатора параллелизма для C\+\+.|  
|[Справочник по библиотеке C](../profiling/c-library-reference.md)|Описывает API визуализатора параллелизма для C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Описывает API визуализатора параллелизма для управляемого кода.|  
|[Визуализатор параллелизма](../profiling/concurrency-visualizer.md)|Справочные сведения по представлениям и отчетам файлов данных профилирования, которые создаются с помощью метода параллелизма и включают данные выполнения потоков.|