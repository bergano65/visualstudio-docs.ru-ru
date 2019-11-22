---
title: Шаг 4. Создание макета формы с помощью элемента управления TableLayoutPanel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54e4713abef096d5a23cf1ebf74a9d90db0d6409
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295730"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Шаг 4. Создание макета формы с помощью элемента управления TableLayoutPanel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

На этом шаге в форму добавляется элемент управления `TableLayoutPanel`. TableLayoutPanel помогает должным образом выровнять элементы управления в форме, которая будет добавлена позднее.

 ![link to video](../data-tools/media/playvideo.gif "PlayVideo")For a video version of this topic, see [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 2](https://go.microsoft.com/fwlink/?LinkId=205211) or [Tutorial 1: Create a Picture Viewer in C# - Video 2](https://go.microsoft.com/fwlink/?LinkId=205200). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Создание макета формы с помощью элемента управления TableLayoutPanel

1. On the left side of the Visual Studio IDE, locate the **Toolbox** tab. Choose the **Toolbox** tab, and the Toolbox appears. (Кроме того, можно выбрать в строке меню **Вид**, **Панель элементов**.)

2. Выберите маленький треугольник рядом с группой **Контейнеры**, чтобы открыть ее, как показано на рисунке ниже.

     ![Containers group](../ide/media/express-toolbox.png "Express_Toolbox") Containers group

3. В форму можно добавить такие элементы управления, как кнопки, флажки и метки. Дважды щелкните значок элемента управления `TableLayoutPanel` на панели элементов. (Or, you can drag the control from the toolbox onto the form.) When you do this, the IDE adds a `TableLayoutPanel` control to your form, as shown in the following picture.

     ![TableLayoutPanel control](../ide/media/express-formtablelayout.png "Express_FormTableLayout") TableLayoutPanel control

    > [!NOTE]
    > После добавления элемента управления TableLayoutPanel, если внутри формы появляется окно с заголовком **Задачи TableLayoutPanel**, чтобы закрыть его, щелкните в любом месте внутри формы. Далее в этом руководстве приводятся сведения об этом окне.

     Обратите внимание, как разворачивается панель элементов, чтобы закрыть форму при нажатии на ее вкладку, и закрывается, после щелчка за ее пределами. Это функция автоматического скрытия интегрированной среды разработки. Ее можно включить или выключить для любого из окон путем нажатия значка канцелярской кнопки в правом верхнем углу окна, чтобы включить автоматическое скрытие и закрепление на месте. Появляется значок канцелярской кнопки, как показано на рисунке ниже.

     ![Pushpin icon](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox") Pushpin icon

4. Убедитесь, что элемент управления **TableLayoutPanel** выделен, щелкнув его. Чтобы убедиться, что элемент управления выделен, необходимо посмотреть на раскрывающийся список в верхней части окна **Свойства**, как показано на рисунке ниже.

     ![Properties window showing TableLayoutPanel control](../ide/media/express-controlspropwin.png "Express_ControlsPropWin") Properties window showing TableLayoutPanel control

5. Нажмите кнопку **В алфавитном порядке** на панели инструментов в окне **Свойства**. Это приведет к отображению списка свойств в окне **Свойства** в алфавитном порядке, что упрощает поиск свойств в этом учебнике.

6. Селектор элементов управления представляет собой раскрывающийся список в верхней части окна **Свойства**. В этом примере он показывает, что выбран элемент управления с именем `tableLayoutPanel1`. Элементы управления можно выбирать, либо выделяя область в конструкторе Windows Forms, либо выбирая их в селекторе элементов управления. Теперь, когда элемент управления `TableLayoutPanel` выбран, найдите свойство **Dock** и выберите **Dock**, значение которого должно быть равным **None**. Обратите внимание, что рядом со значением появляется стрелка раскрывающегося списка. Нажмите стрелку, затем нажмите кнопку **Заполнение** (большая кнопка в середине), как показано на рисунке ниже.

     ![Properties window with Fill selected](../ide/media/express-docktable.png "Express_DockTable") Properties window with Fill selected

     Под *закреплением* в Visual Studio понимается прикрепление окна к другому окну или области в интегрированной среде разработки. Например, окно свойств можно оставить неприкрепленным в пределах окна Visual Studio или же закрепить в области **Обозреватель решений**.

7. После того как у элемента управления TableLayoutPanel свойству **Dock** будет присвоено значение **Fill**, панель заполнит всю форму. Если снова изменить размер формы, элемент управления TableLayoutPanel останется закрепленным и сам изменит свой размер для заполнения формы.

    > [!NOTE]
    > Элемент управления TableLayoutPanel работает как таблица в Microsoft Office Word — он содержит строки и столбцы и отдельная ячейка может занимать несколько строк и столбцов. Каждая ячейка может содержать один элемент управления (например, кнопку, флажок или метку). Этот элемент управления TableLayoutPanel будет содержать элемент управления `PictureBox`, который займет всю верхнюю строку, элемент управления `CheckBox` в левой нижней ячейке, и четыре элемента управления `Button` в правой нижней ячейке.

8. В данный момент элемент управления TableLayoutPanel содержит две одинаковые по размеру строки и два одинаковых по размеру столбца. Нужно изменить их размер, чтобы верхняя строка и правый столбец были намного больше. В конструкторе Windows Forms выберите элемент управления TableLayoutPanel. В правом верхнем углу расположена маленькая кнопка с черным треугольником, как показано на рисунке ниже.

     ![Triangle button](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle") Triangle button

     Это кнопка указывает, что элемент управления содержит задачи, которые помогут автоматически задать его свойства.

9. Чтобы отобразить список задач элемента управления, как показано на рисунке ниже, нажмите треугольник.

     ![TableLayoutPanel tasks](../ide/media/express-tablepanel.png "Express_TablePanel") TableLayoutPanel tasks

10. Выберите задачу **Изменить строки и столбцы**, чтобы открыть окно **Стили столбцов и строк**. Выберите **Столбец1**, убедитесь, что нажата кнопка **Проценты**, установите его размер равным 15 процентам — введите `15` в поле **Проценты**. (That's a `NumericUpDown` control, which you will use in a later tutorial.) Choose **Column2** and set it to 85 percent. Пока не нажимайте кнопку **ОК**, так как окно будет закрыто. (но если это было сделано, его можно открыть повторно с помощью списка задач).

     ![TableLayoutPanel column and row styles](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup") TableLayoutPanel column and row styles

11. В раскрывающемся списке **Показать** в верхней части окна выберите **Строки**. Задайте для **Row1** значение 90 процентов, а для **Row2** 10 процентов.

12. Нажмите кнопку **ОК** . Элемент управления TableLayoutPanel теперь должен содержать большую верхнюю строку, маленькую нижнюю строку, маленький левый столбец и большой правый столбец. Можно изменить размер строк и столбцов в элементе управления TableLayoutPanel, выбрав tableLayoutPanel1 в форме, а затем перетащив границы его строк и столбцов.

     ![Form1 with resized TableLayoutPanel](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel") Form1 with resized TableLayoutPanel

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Следующий шаг руководства см. в разделе [Шаг 5. Добавление элементов управления в форму](../ide/step-5-add-controls-to-your-form.md).

- Предыдущий шаг руководства см. в разделе [Шаг 3. Задание свойств формы](../ide/step-3-set-your-form-properties.md).
