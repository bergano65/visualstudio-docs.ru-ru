---
title: Создание пользовательских данных визуализаторов | Документация Майкрософт
ms.date: 11/07/2018
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048954"
---
# <a name="create-custom-data-visualizers"></a>Создание пользовательских данных визуализаторов
 Объект *визуализатор* является частью [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] пользовательский интерфейс отладчика, который отображает переменной или объекта способом, подходящим для этого типа данных. Например HTML-визуализатор интерпретирует строку HTML и отображает результат, отображаемое в окне браузера. Визуализатор точечных рисунков распознает структуру точечного рисунка и отображает представляемой им. Некоторые визуализаторы позволяют изменить, а также просматривать данные.

 Отладчик [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] включает шесть стандартных визуализаторов. Текст, HTML, XML и JSON визуализаторы работающие со строковыми объектами. Визуализатор дерева WPF отображает свойства визуального дерева объекта WPF. Средство визуализации наборов данных работает для объектов DataSet, DataView и DataTable.

Дополнительные визуализаторы могут быть доступны для загрузки из Майкрософт, сторонними производителями и сообществом. Можно также создавать собственные визуализаторы и устанавливать их в [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] отладчика.

В отладчике, визуализатор представлен значок увеличительного стекла ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор"). Можно выбрать значок в **DataTip**, отладчик **Watch** окна, или **"Быстрая проверка"** диалоговое окно, а затем выберите соответствующий визуализатор для соответствующего объекта.

## <a name="write-custom-visualizers"></a>Запись пользовательских визуализаторов

 > [!NOTE]
 > Чтобы создать пользовательский визуализатор для машинного кода, см. в разделе [SQLite собственного визуализатор отладчика](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) образца. Пользовательские визуализаторы не поддерживаются для приложений для универсальной платформы Windows и Windows 8.x.

Пользовательский визуализатор можно создать для объекта любого управляемого класса, за исключением <xref:System.Object> и <xref:System.Array>.

Архитектура визуализатора отладчика состоит из двух частей:

- *Сторона отладчика* запускается в отладчике Visual Studio и создает и отображает пользовательский интерфейс визуализатора.

- *Сторона отлаживаемого кода* — код, который выполняется внутри процесса, отлаживаемого в Visual Studio (*отлаживаемая* программа). Объект данных для визуализации (например, строковый объект) существует в отлаживаемом процессе. Отлаживаемый объект передает объект на стороне отладчика, которая отображается в пользовательском интерфейсе, создаваемых.

Сторона отладчика получает объект данных из *поставщик объектов* , реализующий <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> интерфейс. Отлаживаемый объект передает объекту, используя *источника объекта*, который является производным от <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

Поставщик объектов может также отправлять данные обратно к источнику объекта, который позволяет написать визуализатор, можно изменять данные. Необходимо переопределить поставщик объектов, связавшись с вычислитель выражений и источника объектов.

Отлаживаемая и отладочная стороны взаимодействуют друг с другом через <xref:System.IO.Stream> методы, выполняющие сериализацию данных объекта в <xref:System.IO.Stream> и десериализации <xref:System.IO.Stream> обратно в объект данных.

Можно написать визуализатор для универсального типа, только в том случае, если тип является открытым типом. Ограничения накладываются те же, что и при использовании атрибута `DebuggerTypeProxy`. Дополнительные сведения см. в разделе [использование атрибута DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).

При работе с пользовательскими визуализаторами следует учитывать вопросы безопасности. См. в разделе [вопросы безопасности визуализатора](../debugger/visualizer-security-considerations.md).

Следующие действия предоставляют общий обзор создания визуализатора. Подробные инструкции см. в разделе [Пошаговое руководство: Написание визуализатора на C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) или [Пошаговое руководство: Написание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>Создание кода для отладочной стороны

Чтобы создать пользовательский интерфейс визуализатора на стороне отладчика, создайте класс, наследуемый от <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>и Переопределите <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> метод для отображения интерфейса. Можно использовать <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> для отображения форм, диалоговых окон и элементов управления Windows в визуализатора.

1. Используйте методы <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> для получения визуализированного объекта на стороне отладчика.

1. Создайте класс, который наследует от <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.

1. Переопределите метод <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> для отображения интерфейса. Используйте <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> методы для отображения форм Windows, диалоговых окон и элементов управления в интерфейсе.

4. Применить <xref:System.Diagnostics.DebuggerVisualizerAttribute>, задавая ему визуализатор для отображения (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>Создание кода для отлаживаемого объекта

Укажите код отлаживаемого объекта с помощью <xref:System.Diagnostics.DebuggerVisualizerAttribute>.

1. Используйте <xref:System.Diagnostics.DebuggerVisualizerAttribute>, предоставив ему визуализатор (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) и источник объекта (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Если опустить источника объекта визуализатора будет использовать источник объекта по умолчанию.

1. Чтобы разрешить изменение, а также отображать объекты данных визуализатор, переопределить `TransferData` или `CreateReplacementObject` методы из <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

## <a name="see-also"></a>См. также

- [Пошаговое руководство: создание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Пошаговое руководство: создание визуализатора на Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)
- [Практическое руководство. Тестирование и отладка визуализатора](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Справочные сведения о программном интерфейсе визуализаторов](../debugger/visualizer-api-reference.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)