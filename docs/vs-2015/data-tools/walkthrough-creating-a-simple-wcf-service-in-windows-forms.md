---
title: 'Пошаговое руководство: Создание простой службы WCF в Windows Forms | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e14944157a14be4a5e06c26464a4de2cdb2bff1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559577"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Пошаговое руководство: Создание простой службы WCF в Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: создание простой службы WCF в Windows Forms](https://docs.microsoft.com/visualstudio/data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms).  
  
  
В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], ее тестирование и последующий доступ к ней из приложения Windows Forms.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Создание службы  
  
#### <a name="to-create-a-wcf-service"></a>Создание простой службы WCF  
  
1.  В меню **Файл** выберите пункт **Создать** , а затем команду **Проект**.  
  
2.  В **новый проект** диалогового окна разверните узел **Visual Basic** или **Visual C#** узел и нажмите кнопку **WCF**, за которым следует **WCF Библиотека службы**. Нажмите кнопку **ОК** для открытия проекта.  
  
     ![Проект библиотеки служб WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Будет создана работающая служба, которую можно протестировать и использовать. Следующие два действия демонстрируют, как можно изменить метод по умолчанию для использования другого типа данных. В реальном приложении необходимо также добавить к службе ее специальные функции.  
  
3.  ![В файле IService1](../data-tools/media/wcf2.png "wcf2")  
  
     В **обозревателе решений**, дважды щелкните файл IService1.vb или IService1.cs и найдите следующую строку:  
  
     [! code-csharp [WCFWalkthrough № 4] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/CS/IService1 (2).cs 4)] [! кода — vb [WCFWalkthrough № 4] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/IService1 (2).vb 4)]  
  
     Измените тип параметра `value` на `String`:  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     В приведенном выше коде обратите внимание на атрибуты `<OperationContract()>` или `[OperationContract]` . Эти атрибуты обязательны для любого метода, предоставляемого службой.  
  
4.  ![Файл Service1](../data-tools/media/wcf3.png "wcf3")  
  
     В **обозревателе решений**, дважды щелкните файл Service1.vb или Service1.cs и найдите следующую строку:  
  
     [! code-csharp [WCFWalkthrough #5] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/CS/Service1 (2).cs #5)] [! кода — vb [WCFWalkthrough #5] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/Service1 (2).vb #5)]  
  
     Измените тип параметра значения на `String`:  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>Тестирование службы  
  
#### <a name="to-test-a-wcf-service"></a>Создание простой службы WCF  
  
1.  Нажмите клавишу **F5** для запуска службы. Объект **тестовый клиент WCF** открывается форма, которая загрузит службу.  
  
2.  В **тестовый клиент WCF** форме, дважды щелкните **GetData()** метод **IService1**. **GetData** будет открыта вкладка.  
  
     ![GetData&#40; &#41; метод](../data-tools/media/wcf4.png "wcf4")  
  
3.  В **запроса** выберите **значение** поле и тип `Hello`.  
  
     ![Поле значения](../data-tools/media/wcf5.png "wcf5")  
  
4.  Нажмите кнопку **Invoke** кнопки. Если **предупреждение системы безопасности** диалоговое окно отображается, щелкните **ОК**. Результат будет отображаться в **ответа** поле.  
  
     ![Результат в поле ответа](../data-tools/media/wcf6.png "wcf6")  
  
5.  На **файл** меню, щелкните **выхода** чтобы закрыть тестовую форму.  
  
## <a name="accessing-the-service"></a>Доступ к службе  
  
#### <a name="to-reference-a-wcf-service"></a>Обращение к службе WCF  
  
1.  На **файл** последовательно выберите пункты **добавить** и нажмите кнопку **новый проект**.  
  
2.  В **новый проект** диалогового окна последовательно раскройте элементы **Visual Basic** или **Visual C#** узел и выберите **Windows**, а затем выберите **Windows Forms Application**. Нажмите кнопку **ОК** для открытия проекта.  
  
     ![Проект приложения Windows Forms](../data-tools/media/wcf7.png "wcf7")  
  
3.  Щелкните правой кнопкой мыши **WindowsApplication1** и нажмите кнопку **Add Service Reference**. **Add Service Reference** появится диалоговое окно.  
  
4.  В **Add Service Reference** диалоговом окне щелкните **Discover**.  
  
     ![В диалоговом окне Add Service Reference](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** будет отображаться в **служб** области.  
  
5.  Нажмите кнопку **ОК** Добавление ссылки на службу.  
  
#### <a name="to-build-a-client-application"></a>Создание клиентского приложения  
  
1.  В **обозревателе решений**, дважды щелкните **Form1.vb** или **Form1.cs** чтобы открыть конструктор Windows Forms, если он еще не открыт.  
  
2.  Из **элементов**, перетащите `TextBox` управления `Label` элемента управления и `Button` на форму.  
  
     ![Добавление элементов управления в форму](../data-tools/media/wcf9.png "wcf9")  
  
3.  Дважды щелкните `Button` и добавьте следующий код в обработчик событий `Click`:  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  В **обозревателе решений**, щелкните правой кнопкой мыши **WindowsApplication1** и нажмите кнопку **Назначить запускаемым проектом**.  
  
5.  Нажмите клавишу **F5** для запуска проекта. Введите любой текст и нажмите кнопку. Будет отображена надпись «Введено:» с введенным ранее текстом.  
  
     ![Форма с результатом](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>См. также  
 [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

