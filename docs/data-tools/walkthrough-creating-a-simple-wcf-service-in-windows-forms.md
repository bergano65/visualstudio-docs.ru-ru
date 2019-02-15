---
title: Пошаговое руководство. Создание простой службы WCF в Windows Forms
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 08b55652fbadd0b27f4519b94e083409c9de3af5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951115"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Пошаговое руководство: Создание простой службы WCF в Windows Forms

В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], ее тестирование и последующий доступ к ней из приложения Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Создание службы

### <a name="to-create-a-wcf-service"></a>Создание простой службы WCF

1.  В меню **Файл** выберите пункт **Создать** , а затем команду **Проект**.

2.  В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C#** и щелкните **WCF** и **Библиотека службы WCF**. Нажмите кнопку **ОК**, чтобы открыть проект.

     ![Проект библиотеки служб WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Будет создана работающая служба, которую можно протестировать и использовать. Следующие два действия демонстрируют, как можно изменить метод по умолчанию для использования другого типа данных. В реальном приложении необходимо также добавить к службе ее специальные функции.

3.  ![Файл IService1](../data-tools/media/wcf2.png)

     В **Обозревателе решений** дважды щелкните файл **IService1.vb** или **IService1.cs** и найдите следующую строку:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Измените тип для `value` параметр в строку:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     В приведенном выше коде обратите внимание на атрибуты `<OperationContract()>` или `[OperationContract]` . Эти атрибуты обязательны для любого метода, предоставляемого службой.

4.  ![Файл Service1](../data-tools/media/wcf3.png)

     В **Обозревателе решений** дважды щелкните файл **Service1.vb** или **Service1.cs** и найдите следующую строку:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Измените тип для `value` параметр в строку:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Тестирование службы

### <a name="to-test-a-wcf-service"></a>Создание простой службы WCF

1.  Нажмите клавишу **F5**, чтобы запустить службу. Объект **тестовый клиент WCF** формы отображается, а сама служба.

2.  В форме **Тестовый клиент WCF** дважды щелкните метод **GetData()** в разделе **IService1**. **GetData** появится вкладка.

     ![GetData&#40; &#41; метод](../data-tools/media/wcf4.png)

3.  В диалоговом окне **Запрос** выберите поле **Значение** и введите `Hello`.

     ![Поле значения](../data-tools/media/wcf5.png)

4.  Нажмите кнопку **Вызвать**. Если **предупреждение системы безопасности** появится диалоговое окно, нажмите кнопку **ОК**. Отображает результат в **ответа** поле.

     ![Результат в поле "Ответ"](../data-tools/media/wcf6.png)

5.  В меню **Файл** щелкните **Выход**, чтобы закрыть тестовую форму.

## <a name="access-the-service"></a>Доступ к службе

### <a name="to-reference-a-wcf-service"></a>Обращение к службе WCF

1.  В меню **Файл** выберите команду **Добавить**, а затем **Создать проект**.

2.  В **новый проект** диалогового окна последовательно раскройте элементы **Visual Basic** или **Visual C#**  выберите **Windows**, а затем выберите  **Windows Forms Application**. Нажмите кнопку **ОК**, чтобы открыть проект.

     ![Проект приложения Windows Forms](../data-tools/media/wcf7.png)

3.  Щелкните правой кнопкой мыши **WindowsApplication1** и выберите команду **Добавить ссылку на службу**. **Add Service Reference** откроется диалоговое окно.

4.  В диалоговом окне **Добавление ссылки на службу** щелкните элемент **Найти**.

     ![Добавить ссылку на службу - диалоговое окно](../data-tools/media/wcf8.png)

     **Service1** отображает в **служб** области.

5.  Нажмите кнопку **ОК**, чтобы добавить ссылку на службу.

### <a name="to-build-a-client-application"></a>Создание клиентского приложения

1.  В **Обозревателе решений** дважды щелкните **Form1.vb** или **Form1.cs**, чтобы открыть конструктор Windows Forms, если он еще не открыт.

2.  Из **Панели элементов** перетащите на форму элемент управления `TextBox`, элемент управления`Label` и элемент управления `Button`.

     ![Добавление элементов управления на форму](../data-tools/media/wcf9.png)

3.  Дважды щелкните `Button` и добавьте следующий код в обработчик событий `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  В **Обозревателе решений** щелкните правой кнопкой мыши **WindowsApplication1** и выберите команду **Назначить запускаемым проектом**.

5.  Нажмите клавишу **F5**, чтобы запустить проект. Введите любой текст и нажмите кнопку. Метка отображает «введено:» и отображается текст, что вы ввели.

     ![Форма с результатом](../data-tools/media/wcf10.png)

## <a name="see-also"></a>См. также

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)