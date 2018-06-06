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
ms.openlocfilehash: 7c9fd9337682abbcd7325a849b95846be3af118d
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747184"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Пошаговое руководство: Создание простой службы WCF в Windows Forms
В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], ее тестирование и последующий доступ к ней из приложения Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="creating-the-service"></a>Создание службы

#### <a name="to-create-a-wcf-service"></a>Создание простой службы WCF

1.  В меню **Файл** выберите пункт **Создать** , а затем команду **Проект**.

2.  В **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#** и выберите команду **WCF**, за которым следует **WCF Библиотека службы**. Нажмите кнопку **ОК** для открытия проекта.

     ![Проект библиотеки служб WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Будет создана работающая служба, которую можно протестировать и использовать. Следующие два действия демонстрируют, как можно изменить метод по умолчанию для использования другого типа данных. В реальном приложении необходимо также добавить к службе ее специальные функции.

3.  ![Файл IService1](../data-tools/media/wcf2.png)

     В **обозревателе решений**, дважды щелкните файл IService1.vb или IService1.cs и найдите следующую строку:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Измените тип для `value` параметра строку:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     В приведенном выше коде обратите внимание на атрибуты `<OperationContract()>` или `[OperationContract]` . Эти атрибуты обязательны для любого метода, предоставляемого службой.

4.  ![Файл Service1](../data-tools/media/wcf3.png)

     В **обозревателе решений**, дважды щелкните файл Service1.vb или Service1.cs и найдите следующую строку:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Измените тип параметра значения на строку:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="testing-the-service"></a>Тестирование службы

#### <a name="to-test-a-wcf-service"></a>Создание простой службы WCF

1.  Нажмите клавишу **F5** для запуска службы. Объект **тестовый клиент WCF** будет показана форма, которая загрузит службу.

2.  В **тестовый клиент WCF** форме, дважды щелкните **GetData()** метод **IService1**. **GetData** будет открыта вкладка.

     ![GetData&#40; &#41; метод](../data-tools/media/wcf4.png)

3.  В **запроса** выберите **значение** и введите `Hello`.

     ![Поле значения](../data-tools/media/wcf5.png)

4.  Нажмите кнопку **Invoke** кнопки. Если **предупреждение системы безопасности** отображается диалоговое окно, нажмите кнопку **ОК**. Результат будет отображаться в **ответ** поле.

     ![Результат в поле "Ответ"](../data-tools/media/wcf6.png)

5.  На **файл** меню, нажмите кнопку **выхода** чтобы закрыть тестовую форму.

## <a name="accessing-the-service"></a>Доступ к службе

#### <a name="to-reference-a-wcf-service"></a>Обращение к службе WCF

1.  На **файл** последовательно выберите пункты **добавить** и нажмите кнопку **новый проект**.

2.  В **новый проект** диалогового окна разверните **Visual Basic** или **Visual C#** , а затем выберите **Windows**, а затем выберите **Приложения Windows Forms в**. Нажмите кнопку **ОК** для открытия проекта.

     ![Проект приложения Windows Forms](../data-tools/media/wcf7.png)

3.  Щелкните правой кнопкой мыши **WindowsApplication1** и нажмите кнопку **добавить ссылку на службу**. **Добавить ссылку на службу** появится диалоговое окно.

4.  В **добавить ссылку на службу** диалоговое окно, нажмите кнопку **Discover**.

     ![Добавить ссылку на службу - диалоговое окно](../data-tools/media/wcf8.png)

     **Service1** будет отображаться в **служб** области.

5.  Нажмите кнопку **ОК** для добавления ссылки на службу.

#### <a name="to-build-a-client-application"></a>Создание клиентского приложения

1.  В **обозревателе решений**, дважды щелкните **Form1.vb** или **Form1.cs** открыть конструктор Windows Forms, если он еще не открыт.

2.  Из **элементов**, перетащите `TextBox` управления `Label` управления и `Button` в форму элемент управления.

     ![Добавление элементов управления на форму](../data-tools/media/wcf9.png)

3.  Дважды щелкните `Button` и добавьте следующий код в обработчик событий `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  В **обозревателе решений**, щелкните правой кнопкой мыши **WindowsApplication1** и нажмите кнопку **Назначить запускаемым проектом**.

5.  Нажмите клавишу **F5** для запуска проекта. Введите любой текст и нажмите кнопку. Будет отображена надпись «Введено:» с введенным ранее текстом.

     ![Форма с результатом](../data-tools/media/wcf10.png)

## <a name="see-also"></a>См. также

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)