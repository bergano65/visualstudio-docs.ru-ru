---
title: "Практическое руководство. Использование пакета SDK визуализатора параллелизма для создания маркеров | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 1a51a8dbf28be35febf4a0954a997e542ffd0f09
ms.openlocfilehash: a05e0509ec092f810e0990fbc838707d126595e1
ms.contentlocale: ru-ru
ms.lasthandoff: 05/19/2017

---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Практическое руководство. Использование пакета SDK визуализатора параллелизма для создания маркеров
В этом разделе содержатся сведения об использовании SDK визуализатора параллелизма для создания интервалов и записи флагов, сообщений и оповещений.  
  
### <a name="to-use-c"></a>Использование C++  
  
1.  Добавьте поддержку пакета SDK визуализатора параллелизма в ваше приложение. Дополнительные сведения см. в статье [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md) (Пакет SDK визуализатора параллелизма).  
  
2.  Добавьте оператор `include` и оператор `using` для пакета SDK.  
  
    ```C++  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Добавьте код для создания трех интервалов в последовательностях маркеров по умолчанию и записи флага, сообщения и оповещения (по одному для каждого диапазона). Методы для написания флагов, сообщений и оповещений являются членами класса [marker_series](../profiling/marker-series-class.md). Конструктору для класса [span](../profiling/span-class.md) требуется объект `marker_series`, чтобы каждый интервал был связан с конкретными последовательностями маркеров. `span` заканчивается, когда он является удаленным.  
  
    ```C++  
  
    marker_series series;  
    span *flagSpan = new span(series, 1, _T("flag span"));  
    series.write_flag(_T("Here is the flag."));  
    delete flagSpan;  
  
    span *messageSpan = new span(series, 2, _T("message span"));  
    series.write_flag(_T("Here is the message."));  
    delete messageSpan;  
  
    span *alertSpan = new span(series, 3, _T("alert span"));  
    series.write_flag(_T("Here is the alert."));  
    delete alertSpan;  
  
    ```  
  
4.  В строке меню выберите **Анализ**, **Визуализатор параллелизма**, **Запустить с текущим проектом**, чтобы запустить приложение и открыть визуализатор параллелизма. На следующем рисунке показаны три интервала и три маркера в визуализаторе параллелизма.  
  
     ![Визуализатор параллелизма с тремя маркерами и оповещениями](~/profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Добавьте код для создания дополнительных пользовательских последовательностей маркеров, вызвав конструктор для `marker_series`, который принимает имя строки для последовательностей маркеров.  
  
    ```C++  
  
    marker_series flagSeries(_T("flag series"));  
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));  
    flagSeries.write_flag(1, _T("flag"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete flagSeriesSpan;  
  
    marker_series messageSeries(_T("message series"));  
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));  
    messageSeries.write_message(1, _T("message"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete messageSeriesSpan;  
  
    ```  
  
6.  Запустите текущий проект, чтобы открыть визуализатор параллелизма. Две последовательности маркеров отображаются на собственных дорожках в представлении потоков. На следующем рисунке показаны два новых интервала.  
  
     ![Визуализатор параллелизма с тремя пользовательскими последовательностями маркеров](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Использование Visual Basic или C# #
  
1.  Добавьте поддержку пакета SDK визуализатора параллелизма в ваше приложение. Дополнительные сведения см. в статье [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md) (Пакет SDK визуализатора параллелизма).  
  
2.  Добавьте оператор `using` или `Imports` для пакета SDK.  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```CSharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Добавьте код для создания трех интервалов в последовательностях маркеров по умолчанию и записи флага, сообщения и оповещения (по одному для каждого диапазона). Объект <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> можно создать путем вызова статического метода [EnterSpan](assetId:///EnterSpan?qualifyHint=False&autoUpgrade=True). Для записи ряда по умолчанию используйте статические методы записи класса <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers>.  
  
    ```VB  
  
    Dim flagSpan As Span = Markers.EnterSpan("flag span")  
    Markers.WriteFlag("Here is the flag.")  
    flagSpan.Leave()  
  
    Dim messageSpan As Span = Markers.EnterSpan("message span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteMessage("Here is a message")  
    messageSpan.Leave()  
  
    Dim alertSpan As Span = Markers.EnterSpan("alert span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteAlert("Here is an alert")  
    alertSpan.Leave()  
  
    ```  
  
    ```CSharp  
  
    Span flagSpan = Markers.EnterSpan("flag span");  
    Markers.WriteFlag("Here is the flag.");  
    flagSpan.Leave();  
  
    Span messageSpan = Markers.EnterSpan("message span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteMessage("Here is a message");  
    messageSpan.Leave();  
  
    Span alertSpan = Markers.EnterSpan("alert span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteAlert("Here is an alert");  
    alertSpan.Leave();  
    ```  
  
4.  В строке меню выберите **Анализ**, **Визуализатор параллелизма**, **Запустить с текущим проектом**, чтобы запустить приложение и открыть визуализатор параллелизма. На следующем рисунке показаны три интервала и три маркера в представлении потоков в визуализаторе параллелизма.  
  
     ![Визуализатор параллелизма с маркерами и оповещениями](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Добавьте код для создания ряда маркеров клиента с помощью статического метода <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A>. Класс <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> содержит методы для создания диапазонов и флагов записи, сообщений и предупреждения.  
  
    ```VB  
  
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")  
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")  
    System.Threading.Thread.Sleep(1)  
    flagSeries.WriteFlag(1, "flag")  
    System.Threading.Thread.Sleep(1)  
    flagSeriesSpan.Leave()  
  
    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")  
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")  
    messageSeries.WriteMessage("message")  
    System.Threading.Thread.Sleep(1)  
    messageSeriesSpan.Leave()  
    ```  
  
    ```CSharp  
  
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");  
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");  
    System.Threading.Thread.Sleep(1);  
    flagSeries.WriteFlag(1, "flag");  
    System.Threading.Thread.Sleep(1);  
    flagSeriesSpan.Leave();  
  
    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");  
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");  
    messageSeries.WriteMessage("message");  
    System.Threading.Thread.Sleep(1);  
    messageSeriesSpan.Leave();  
    ```  
  
6.  Запустите текущий проект, чтобы открыть визуализатор параллелизма. Три последовательности маркеров отображаются на собственных дорожках в представлении потоков. На следующем рисунке показаны три новых интервала.  
  
     ![Визуализатор параллелизма с тремя пользовательскими последовательностями маркеров](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesNative")  
  
## <a name="see-also"></a>См. также  
 [Пакет SDK визуализатора параллелизма](../profiling/concurrency-visualizer-sdk.md)

