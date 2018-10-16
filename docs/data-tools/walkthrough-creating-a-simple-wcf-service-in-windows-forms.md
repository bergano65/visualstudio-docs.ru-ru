---
title: 'Пошаговое руководство: Создание простой службы WCF в Windows Forms'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2c9d0bd58adcd0a0595c061fa4dfaa81f629601
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174251"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Пошаговое руководство: Создание простой службы WCF в Windows Forms

В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], ее тестирование и последующий доступ к ней из приложения Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Создание службы

### <a name="to-create-a-wcf-service"></a>Создание простой службы WCF

1.  В меню **Файл** выберите пункт **Создать** , а затем команду **Проект**.

2.  В **новый проект** диалогового окна разверните узел **Visual Basic** или **Visual C#** узел и нажмите кнопку **WCF**, за которым следует **WCF Библиотека службы**. Нажмите кнопку **ОК** для открытия проекта.

     ![Проект библиотеки служб WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Будет создана работающая служба, которую можно протестировать и использовать. Следующие два действия демонстрируют, как можно изменить метод по умолчанию для использования другого типа данных. В реальном приложении необходимо также добавить к службе ее специальные функции.

3.  ![Файл IService1](../data-tools/media/wcf2.png)

     В **обозревателе решений**, дважды щелкните **IService1.vb** или **IService1.cs** и найдите следующую строку:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Измените тип для `value` параметр в строку:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     В приведенном выше коде обратите внимание на атрибуты `<OperationContract()>` или `[OperationContract]` . Эти атрибуты обязательны для любого метода, предоставляемого службой.

4.  ![Файл Service1](../data-tools/media/wcf3.png)

     В **обозревателе решений**, дважды щелкните **Service1.vb** или **Service1.cs** и найдите следующую строку:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Измените тип для `value` параметр в строку:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Тестирование службы

### <a name="to-test-a-wcf-service"></a>Создание простой службы WCF

1.  Нажмите клавишу **F5** для запуска службы. Объект **тестовый клиент WCF** формы отображается, а сама служба.

2.  В **тестовый клиент WCF** форме, дважды щелкните **GetData()** метод **IService1**. **GetData** появится вкладка.

     ![GetData&#40; &#41; метод](../data-tools/media/wcf4.png)

3.  В **запроса** выберите **значение** поле и тип `Hello`.

     ![Поле значения](../data-tools/media/wcf5.png)

4.  Нажмите кнопку **Invoke** кнопки. Если **предупреждение системы безопасности** появится диалоговое окно, нажмите кнопку **ОК**. Отображает результат в **ответа** поле.

     ![Результат в поле "Ответ"](../data-tools/media/wcf6.png)

5.  На **файл** меню, щелкните **выхода** чтобы закрыть тестовую форму.

## <a name="access-the-service"></a>Доступ к службе

### <a name="to-reference-a-wcf-service"></a>Обращение к службе WCF

1.  На **файл** последовательно выберите пункты **добавить** и нажмите кнопку **новый проект**.

2.  В **новый проект** диалогового окна последовательно раскройте элементы **Visual Basic** или **Visual C#** выберите **Windows**, а затем выберите  **Windows Forms Application**. Нажмите кнопку **ОК** для открытия проекта.

     ![Проект приложения Windows Forms](../data-tools/media/wcf7.png)

3.  Щелкните правой кнопкой мыши **WindowsApplication1** и нажмите кнопку **Add Service Reference**. **Add Service Reference** откроется диалоговое окно.

4.  В **Add Service Reference** диалоговом окне щелкните **Discover**.

     ![Добавить ссылку на службу - диалоговое окно](../data-tools/media/wcf8.png)

     **Service1** отображает в **служб** области.

5.  Нажмите кнопку **ОК** Добавление ссылки на службу.

### <a name="to-build-a-client-application"></a>Создание клиентского приложения

1.  В **обозревателе решений**, дважды щелкните **Form1.vb** или **Form1.cs** чтобы открыть конструктор Windows Forms, если он еще не открыт.

2.  Из **элементов**, перетащите `TextBox` управления `Label` элемента управления и `Button` на форму.

     ![Добавление элементов управления на форму](../data-tools/media/wcf9.png)

3.  Дважды щелкните `Button` и добавьте следующий код в обработчик событий `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  В **обозревателе решений**, щелкните правой кнопкой мыши **WindowsApplication1** и нажмите кнопку **Назначить запускаемым проектом**.

5.  Нажмите клавишу **F5** для запуска проекта. Введите любой текст и нажмите кнопку. Метка отображает «введено:» и отображается текст, что вы ввели.

     ![Форма с результатом](../data-tools/media/wcf10.png)

## <a name="see-also"></a>См. также

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)