---
title: Руководство. Создание визуализатора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce50276e4e83a1a055294c8e2b6e09cd0f93d54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843265"
---
# <a name="how-to-write-a-visualizer"></a>Практическое руководство. Написание визуализатора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пользовательский визуализатор можно создать для объекта любого управляемого класса, за исключением <xref:System.Object> и <xref:System.Array>.  
  
> [!NOTE]
> В приложениях **магазина** поддерживаются только стандартные визуализаторы Text, HTML, XML и JSON. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
 Архитектура визуализатора отладчика состоит из двух частей:  
  
- *Сторона отладчика* — код, который запускается в отладчике Visual Studio. Код со стороны отладчика создает и отображает пользовательский интерфейс визуализатора.  
  
- *Сторона отлаживаемого кода* — код, который выполняется внутри процесса, отлаживаемого в Visual Studio (*отлаживаемая* программа).  
  
  Объекты данных, которые требуется визуализировать (например, строковые объекты), принадлежат отлаживаемому процессу. Таким образом, отлаживаемая сторона должна передать объект данных стороне отладчика, которая затем может вывести эти данные с помощью созданного пользовательского интерфейса.  
  
  Сторона отладчика получает этот объект данных для визуализации от *поставщика объектов* , реализующего <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> интерфейс. Отлаживаемая сторона отправляет объект данных через *источник объекта*, производный от <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . Поставщик объектов может также отправлять данные обратно к источнику объекта, что позволяет создавать визуализаторы, которые помимо отображения могут также изменять данные. Поставщик объектов может быть переопределен, чтобы контактировать с вычислителем выражений и, следовательно, с источником объектов.  
  
  Отлаживаемая и отладочная стороны взаимодействуют друг с другом через <xref:System.IO.Stream>. Предоставляются методы для сериализации объекта данных в <xref:System.IO.Stream> и десериализации <xref:System.IO.Stream> обратно в объект данных.  
  
  Код отлаживаемого объекта обуславливается с помощью атрибута DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
  Чтобы создать пользовательский интерфейс визуализатора на стороне отладчика, необходимо создать класс, который наследует <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> и переопределить метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса.  
  
  Можно использовать <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> для отображения форм Windows, диалоговых окон и элементов управления из визуализатора.  
  
  Поддержка универсальных типов ограничена. Можно написать визуализатор для целевого универсального типа, только если он является открытым. Ограничения накладываются те же, что и при использовании атрибута `DebuggerTypeProxy`. Дополнительные сведения см. [в разделе Использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
  При работе с пользовательскими визуализаторами следует учитывать вопросы безопасности. См. раздел [вопросы безопасности визуализатора](../debugger/visualizer-security-considerations.md).  
  
  Процедуры, приведенные ниже, дают подробное описание, что необходимо сделать для создания визуализатора. Более подробное описание см. в разделе [Пошаговое руководство. Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Создание кода для отладочной стороны  
  
1. Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> для получения визуализированного объекта на стороне отладчика.  
  
2. Создайте класс, который наследует от <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3. Переопределите метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса. Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> для отображения форм, диалоговых окон и элементов управления Windows как части интерфейса.  
  
4. Используйте <xref:System.Diagnostics.DebuggerVisualizerAttribute>, предоставив ему визуализатор (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Создание кода для отлаживаемого объекта  
  
1. Используйте <xref:System.Diagnostics.DebuggerVisualizerAttribute>, предоставив ему визуализатор (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) и источник объекта (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Если источник объекта не задан, будет использоваться источник объекта, заданный по умолчанию  
  
2. Если необходимо, чтобы визуализатор редактировал объекты данных, помимо их отображения, то необходимо переопределить методы `TransferData` или  `CreateReplacementObject` для <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## <a name="see-also"></a>См. также:  
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)   
 [Тестирование и отладка визуализатора](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Вопросы безопасности визуализатора](../debugger/visualizer-security-considerations.md)
