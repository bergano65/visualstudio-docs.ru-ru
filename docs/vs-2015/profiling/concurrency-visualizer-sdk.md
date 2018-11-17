---
title: Пакет SDK визуализатора параллелизма | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.sdk.about
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d98a5383a330242110bef860b9dc19a2fb6bef87
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754831"
---
# <a name="concurrency-visualizer-sdk"></a>Пакет SDK визуализатора параллелизма
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно инструментировать свой исходный код с помощью пакета SDK визуализатора параллелизма для отображения дополнительных сведений в визуализаторе параллелизма. Можно связать дополнительные данные с этапами выполнения кода и событиями в коде. Эти дополнительные визуализации известны как *маркеры*.  Ознакомительное пошаговое руководство см. в разделе [Сведения о пакете SDK визуализатора параллелизма](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## <a name="properties"></a>Свойства  
 Флаги, интервалы и сообщения имеют по два свойства: "Категория"и "Важность". В диалоговом окне [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) эти свойства можно использовать для фильтрации набора отображаемых маркеров. Кроме того, эти свойства влияют на визуальное представление маркеров. Например, размер флагов используется для представления важности. А цвет используется для указания категории.  
  
## <a name="basic-usage"></a>Основное использование  
 Визуализатор параллелизма предоставляет поставщик по умолчанию, который можно использовать для создания маркеров. Поставщик уже зарегистрирован вместе с визуализатором параллелизма, и никакие дополнительные действия для отображения маркеров в пользовательском интерфейсе не требуются.  
  
### <a name="c-and-visual-basic"></a>C# и Visual Basic  
 В коде на языке C#, Visual Basic или другом управляемом коде используйте поставщик по умолчанию путем вызова <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>. Он предоставляет функции для создания маркеров: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> и <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>. Для этих функций есть несколько перегруженных методов, применяемых в зависимости от того, нужно ли использовать значения по умолчанию для свойства.  Простейшая перегрузка принимает только строковый параметр, который указывает описание события. Описание отображается в отчетах визуализатора параллелизма.  
  
##### <a name="to-add-sdk-support-to-a-c-or-visual-basic-project"></a>Добавление поддержки пакета SDK в проект C# или Visual Basic  
  
1.  В строке меню выберите **Анализ**, **Визуализатор параллелизма**, **Добавить пакет SDK в проект**.  
  
2.  Выберите проект, в котором нужно получить доступ к пакету SDK, а затем нажмите кнопку **Добавить пакет SDK в выбранный проект**.  
  
3.  Добавьте в код оператор imports или using.  
  
    ```csharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### <a name="c"></a>C++  
 В C++ создайте объект [Класс marker_series](../profiling/marker-series-class.md) и используйте его для вызова функций.  Класс `marker_series` предоставляет три функции для создания маркеров: [метод marker_series::write_flag](../profiling/marker-series-write-flag-method.md), [метод marker_series::write_message](../profiling/marker-series-write-message-method.md) и [метод marker_series::write_alert](../profiling/marker-series-write-alert-method.md).  
  
##### <a name="to-add-sdk-support-to-a-c-or-c-project"></a>Добавление поддержки пакета SDK в проект C++ или C  
  
1.  В строке меню выберите **Анализ**, **Визуализатор параллелизма**, **Добавить пакет SDK в проект**.  
  
2.  Выберите проект, в котором нужно получить доступ к пакету SDK, а затем нажмите кнопку **Добавить пакет SDK в выбранный проект**.  
  
3.  Для C++ включите `cvmarkersobj.h`. Для C включите `cvmarkers.h`.  
  
4.  Добавьте в код оператор using.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Создайте объект `marker_series` и передайте его в конструктор `span`.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## <a name="custom-usage"></a>Другие виды использования  
 Для более сложных сценариев пакет SDK визуализатора параллелизма предоставляет больше возможностей управления.  С ними связаны два следующих основных понятия: поставщики маркеров и наборы маркеров. Поставщики маркеров представляют собой различные поставщики трассировки событий Windows (каждый из которых имеет отличающийся от других GUID). Наборы маркеров представляют собой последовательные каналы событий, созданные одним поставщиком. Их можно использовать для организации событий, созданных поставщиком маркеров.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-visual-basic-project"></a>Использование нового поставщика маркера в проекте C# или Visual Basic  
  
1.  Создание объекта <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>.  Конструктор принимает идентификатор GUID.  
  
2.  Чтобы зарегистрировать поставщик, откройте диалоговое окно [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) визуализатора параллелизма.  Выберите вкладку **Маркеры** и нажмите кнопку **Добавить новый поставщик**. В диалоговом окне [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) введите идентификатор GUID, который использовался для создания поставщика, и описание поставщика.  
  
#### <a name="to-use-a-new-marker-provider-in-a-c-or-c-project"></a>Использование нового поставщика маркеров в проекте C# или Visual Basic  
  
1.  Используйте функцию `CvInitProvider` для инициализации PCV_PROVIDER.  Конструктор принимает GUID* и PCV_PROVIDER\*.  
  
2.  Чтобы зарегистрировать поставщик, откройте диалоговое окно [Дополнительные параметры](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Выберите вкладку **Маркеры** и нажмите кнопку **Добавить новый поставщик**. В диалоговом окне введите идентификатор GUID, который использовался для создания поставщика, и описание поставщика.  
  
#### <a name="to-use-a-marker-series-in-a-c-or-visual-basic-project"></a>Использование набора маркеров в проекте C# или Visual Basic  
  
1.  Для использования нового <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> сначала создайте его с помощью объекта <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>, а затем сформируйте события маркеров непосредственно из нового набора.  
  
    ```csharp  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Использование набора маркеров в проекте C++  
  
1.  Создание объекта `marker_series`.  События можно создавать из этого нового набора.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### <a name="to-use-a-marker-series-in-a-c-project"></a>Использование набора маркеров в проекте C  
  
1.  Используйте функцию `CvCreateMarkerSeries` для создания PCV_MARKERSERIES.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Справочник по библиотеке C++](../profiling/cpp-library-reference.md)|Описывает API визуализатора параллелизма для C++.|  
|[Справочник по библиотеке C](../profiling/c-library-reference.md)|Описывает API визуализатора параллелизма для C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Описывает API визуализатора параллелизма для управляемого кода.|  
|[Визуализатор параллелизма](../profiling/concurrency-visualizer.md)|Справочные сведения по представлениям и отчетам файлов данных профилирования, которые создаются с помощью метода параллелизма и включают данные выполнения потоков.|



