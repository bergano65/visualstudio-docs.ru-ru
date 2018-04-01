---
title: Создание настраиваемых средств визуализации данных | Документы Microsoft
ms.custom: ''
ms.date: 06/19/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 23985c56ba61e5a788232523611a48cfde902335
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-visualizers-of-data"></a>Создание настраиваемых средств визуализации данных
 Визуализаторы – это компоненты [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] пользовательского интерфейса отладчика. Объект *визуализатор* создает диалоговое окно или другой элемент интерфейса, в переменной или объекта способом, подходящим для этого типа данных. Например, HTML-визуализатор интерпретирует строку HTML и отображает результат в том виде, в каком она будет выглядеть в окне браузера; визуализатор точечных рисунков распознает структуру точечного рисунка и отображает его. Некоторые визуализаторы позволяют не только просматривать, но и редактировать данные.

 Отладчик [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] включает шесть стандартных визуализаторов. Это текст, HTML, XML и JSON визуализаторы, которые работают со строковыми объектами; Визуализатор дерева WPF для отображения свойств визуального дерева объекта WPF; и визуализатор наборов данных, который работает с объектами DataSet, DataView и DataTable. В будущем могут появиться дополнительные визуализаторы, которые будут доступны для загрузки из корпорации Майкрософт, а также сайтов сторонних компаний и сообщества. Кроме того, вы можете создавать собственные визуализаторы и устанавливать их в отладчик [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

 > [!NOTE]
 > Чтобы создать пользовательский визуализатор для машинного кода, в разделе [SQLite собственного визуализатор отладчика](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) образца. В приложениях 8.x UWP и Windows настраиваемые визуализаторы не поддерживаются.

 В отладчике визуализаторы представлены значок лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор"). Когда появляется значок лупы в **подсказка**, в окне отладчика, например **Контрольные значения** окна, или в **Быстрая проверка** диалоговое окно, щелкните значок лупы, чтобы Выберите визуализатор, подходящий для типа данных соответствующего объекта.

## <a name="overview-of-custom-visualizers"></a>Общие сведения о пользовательских визуализаторов

Пользовательский визуализатор можно создать для объекта любого управляемого класса, за исключением <xref:System.Object> и <xref:System.Array>.  
  
 Архитектура визуализатора отладчика состоит из двух частей:  
  
-   *Сторона отладчика* запускается в отладчике Visual Studio. Код со стороны отладчика создает и отображает пользовательский интерфейс визуализатора.  
  
-   *Отлаживаемая сторона* выполняется внутри процесса, отлаживаемого в Visual Studio ( *отлаживаемого объекта*).  
  
 Объекты данных, которые требуется визуализировать (например, строковые объекты), принадлежат отлаживаемому процессу. Таким образом, отлаживаемая сторона должна передать объект данных стороне отладчика, которая затем может вывести эти данные с помощью созданного пользовательского интерфейса.  
  
 Сторона отладчика получает объект данных для визуализации от *поставщик объектов* , реализующий <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> интерфейса. Отлаживаемая сторона передает объект данных через *источник объекта*, который является производным от <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Поставщик объектов может также отправлять данные обратно к источнику объекта, что позволяет создавать визуализаторы, которые помимо отображения могут также изменять данные. Поставщик объектов может быть переопределен, чтобы контактировать с вычислителем выражений и, следовательно, с источником объектов.  
  
 Отлаживаемая и отладочная стороны взаимодействуют друг с другом через <xref:System.IO.Stream>. Предоставляются методы для сериализации объекта данных в <xref:System.IO.Stream> и десериализации <xref:System.IO.Stream> обратно в объект данных.  
  
 Код отлаживаемой стороны обуславливается с помощью атрибута DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
 Чтобы создать пользовательский интерфейс визуализатора на стороне отладчика, необходимо создать класс, который наследует <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> и переопределить метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса.  
  
 Можно использовать <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> для отображения форм Windows, диалоговых окон и элементов управления из визуализатора.  
  
 Поддержка универсальных типов ограничена. Можно написать визуализатор для целевого универсального типа, только если он является открытым. Ограничения накладываются те же, что и при использовании атрибута `DebuggerTypeProxy`. Дополнительные сведения см. в разделе [с помощью атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 При работе с пользовательскими визуализаторами следует учитывать вопросы безопасности. В разделе [вопросы безопасности визуализатора](../debugger/visualizer-security-considerations.md).  
  
 Процедуры, приведенные ниже, дают подробное описание, что необходимо сделать для создания визуализатора. Более подробное описание см. в разделе [Пошаговое руководство: Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Создание кода для отладочной стороны  
  
1.  Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> для получения визуализированного объекта на стороне отладчика.  
  
2.  Создайте класс, который наследует от <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Переопределите метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса. Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> для отображения форм, диалоговых окон и элементов управления Windows как части интерфейса.  
  
4.  Используйте <xref:System.Diagnostics.DebuggerVisualizerAttribute>, предоставив ему визуализатор (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Создание кода для отлаживаемой стороны  
  
1.  Используйте <xref:System.Diagnostics.DebuggerVisualizerAttribute>, предоставив ему визуализатор (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) и источник объекта (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Если источник объекта не задан, будет использоваться источник объекта, заданный по умолчанию  
  
2.  Если необходимо, чтобы визуализатор редактировал объекты данных, помимо их отображения, то необходимо переопределить методы `TransferData` или  `CreateReplacementObject` для <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="in-this-section"></a>В этом разделе
  
 [Пошаговое руководство. Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Пошаговое руководство. Написание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)  
  
 [Практическое руководство. Тестирование и отладка визуализатора](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Справочные сведения о прикладном программном интерфейсе визуализаторов](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Связанные разделы  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)