---
title: "Пошаговое руководство: Написание визуализатора на Visual Basic | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc15612fe7a59516483bb6b077e1b44b44f7fba8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Пошаговое руководство. Написание визуализатора на Visual Basic
В данном пошаговом руководстве демонстрируется создание простого визуализатора с помощью [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Визуализатор, который будет создан в данном пошаговом руководстве, отображает содержимое строки с помощью окна сообщения Windows Forms. Этот строковый визуализатор – простой пример, на основе которого можно создавать визуализаторы для других типов данных, более подходящих для ваших проектов.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от действующих параметров или выпуска среды. Чтобы изменить параметры, перейдите на **средства** меню и выберите **импорта и экспорта** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Код визуализатора должен быть помещен в библиотеку DLL, которая будет использоваться отладчиком. Первым шагом является создание проекта библиотеки классов для библиотеки DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Создание и подготовка проекта библиотеки классов  
  
#### <a name="to-create-a-class-library-project"></a>Создание проекта библиотеки классов  
  
1.  На **файл** меню, выберите **New** и нажмите кнопку **новый проект**.  
  
2.  В **новый проект** диалогового **тип проекта**s, нажмите кнопку **Visual Basic**.  
  
3.  В **шаблоны** щелкните **библиотеки классов**.  
  
4.  В **имя** введите соответствующее имя для библиотеки класса, такие как **MyFirstVisualizer**.  
  
5.  Нажмите кнопку **ОК**.  
  
 После создания библиотеки классов необходимо добавить ссылку на библиотеку Microsoft.VisualStudio.DebuggerVisualizers.DLL, чтобы иметь возможность использовать определенные там классы. Но сначала следует присвоить проекту понятное имя.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Переименование Class1.vb и добавление Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Class1.vb**и в контекстном меню пункт **переименование**.  
  
2.  Измените имя с Class1.vb на что-нибудь более осмысленное, например DebuggerSide.vb.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически изменит объявление класса в DebuggerSide.vb в соответствии с новым именем файла.  
  
3.  В **обозревателе решений**, щелкните правой кнопкой мыши **My First Visualizer**и в контекстном меню пункт **добавить ссылку**.  
  
4.  В **добавить ссылку** диалогового **.NET** выберите Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Нажмите кнопку **ОК**.  
  
6.  В файле DebuggerSide.vb добавьте следующий оператор к операторам импорта `Imports`:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Добавление кода для отладчика  
 Теперь можно приступить к написанию кода для отладчика. Этот код запускается отладчиком для отображения информации, которую требуется визуализировать. Во-первых, необходимо изменить объявление объекта `DebuggerSide` таким образом, чтобы он наследовал базовый класс `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Наследование от DialogDebuggerVisualizer  
  
1.  В файле DebuggerSide.vb перейдите к следующей строке:  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  Измените код следующим образом:  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 В классе `DialogDebuggerVisualizer` имеется один абстрактный метод `Show`. Этот метод необходимо перегрузить.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Переопределение метода DialogDebuggerVisualizer.Show  
  
-   Добавьте следующий метод в класс `public class DebuggerSide`:  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 Код метода `Show` отвечает за создание диалогового окна визуализатора или другого пользовательского интерфейса, а также за отображение информации, которая была передана визуализатору из отладчика. Необходимо вручную добавить код, который создает диалоговое окно и отображает информацию. В данном пошаговом руководстве для этого используется окно сообщения Windows Forms. Во-первых, необходимо добавить ссылку и оператор `Imports` для импорта пространства имен <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Добавление пространства имен System.Windows.Forms  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ссылки**и в контекстном меню пункт **добавить ссылку**.  
  
2.  В **добавить ссылку** диалогового **.NET** щелкните **System.Windows.Forms**.  
  
3.  Нажмите кнопку **ОК**.  
  
4.  В файле DebuggerSide.cs добавьте следующий оператор к операторам `Imports`:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Создание пользовательского интерфейса визуализатора  
 Сейчас необходимо добавить код для создания и отображения пользовательского интерфейса визуализатора. Поскольку это всего лишь пример, мы ограничимся написанием простого пользовательского интерфейса с использованием стандартного окна сообщений.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Вывод данных визуализатора в диалоговом окне  
  
1.  Добавьте следующую строку кода в метод `Show`:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     В этом примере отсутствует код для обработки ошибок. В реальном визуализаторе, как и в приложении любого другого типа, код обработки ошибок должен присутствовать.  
  
2.  На **построения** меню, нажмите кнопку **построить MyFirstVisualizer**. Построение проекта должно пройти без ошибок. Если при построении все же возникнут ошибки, исправьте их, прежде чем продолжить.  
  
## <a name="add-the-necessary-attribute"></a>Добавление необходимого атрибута  
 Код для отладчика написан. Тем не менее, необходимо выполнить еще одно действие: добавить атрибут, который сообщает отлаживаемому коду, какой набор классов формирует визуализатор.  
  
#### <a name="to-add-the-debugee-side-code"></a>Добавление кода для отлаживаемой стороны  
  
1.  Добавьте следующий код атрибута в файл DebuggerSide.vb, после операторов `Imports`, но перед `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  На **построения** меню, нажмите кнопку **построить MyFirstVisualizer**. Построение проекта должно пройти без ошибок. Если при построении все же возникнут ошибки, исправьте их, прежде чем продолжить.  
  
## <a name="create-a-test-harness"></a>Создание тестового окружения  
 На этом написание вашего первого визуализатора окончено. Если вы правильно следовали описанной выше процедуре, можно построить визуализатор и установить его в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Однако перед установкой визуализатора в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] следует проверить, что он работает правильно. Для этого следует создать тестовое окружение, в котором визуализатор будет запускаться без установки в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Добавление тестового метода для демонстрации визуализатора  
  
1.  Добавьте следующий метод в класс `public DebuggerSide`:  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  На **построения** меню, нажмите кнопку **построить MyFirstVisualizer**. Построение проекта должно пройти без ошибок. Если при построении все же возникнут ошибки, исправьте их, прежде чем продолжить.  
  
 Далее необходимо создать проект исполняемого файла, из которого будет вызваться библиотека DLL визуализатора. Для простоты выберите проект консольного приложения.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Добавление проекта консольного приложения в решение  
  
1.  На **файл** меню, нажмите кнопку **добавить**, а затем нажмите кнопку **новый проект**.  
  
2.  В **Добавление нового проекта** диалогового **шаблоны** щелкните **консольное приложение**.  
  
3.  В **имя** введите понятное имя для консольного приложения, такие как **MyTestConsole**.  
  
4.  Нажмите кнопку **ОК**.  
  
 Теперь необходимо добавить необходимые ссылки, чтобы программа MyTestConsole могла вызывать MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Добавление необходимых ссылок в MyTestConsole  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **MyTestConsole**и в контекстном меню пункт **добавить ссылку**.  
  
2.  В **добавить ссылку** диалогового **.NET** щелкните Microsoft.VisualStudio.DebuggerVisualizers.  
  
3.  Нажмите кнопку **ОК**.  
  
4.  Щелкните правой кнопкой мыши **MyTestConsole**, а затем нажмите кнопку **добавить ссылку** еще раз.  
  
5.  В **добавить ссылку** диалоговое окно, нажмите кнопку **проекты** , а затем выберите MyFirstVisualizer.  
  
6.  Нажмите кнопку **ОК**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Доводка тестового окружения и тестирование визуализатора  
 Теперь нужно добавить код, которым завершится создание тестового окружения.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Добавление кода в MyTestConsole  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Program.vb**и в контекстном меню пункт **переименование**.  
  
2.  Измените имя Module1.vb на что-нибудь подходящее, таких как **TestConsole.vb**.  
  
     Обратите внимание на то, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически изменяет объявление класса в TestConsole.vb в соответствии с новым именем файла.  
  
3.  В TestConsole. VB, добавьте следующий `Imports` инструкции:  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  В метод `Main` добавьте следующий код:  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 Теперь все готово для проверки примера визуализатора.  
  
#### <a name="to-test-the-visualizer"></a>Тестирование визуализатора  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **MyTestConsole**и в контекстном меню пункт **Назначить запускаемым проектом**.  
  
2.  На **отладки** меню, нажмите кнопку **запустить**.  
  
     Будет запущено консольное приложение. Появится окно визуализатора, в котором будет выведена строка "Hello, World".  
  
 Поздравляем! Вы только что создали и протестировали ваш первый визуализатор.  
  
 Если вам удобнее вызывать визуализатор из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], а не из специально подготовленной тестовой программы, визуализатор необходимо установить. Дополнительные сведения см. в разделе [как: Установка визуализатора](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура визуализатора](../debugger/visualizer-architecture.md)   
 [Как: Установка визуализатора](../debugger/how-to-install-a-visualizer.md)   
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)