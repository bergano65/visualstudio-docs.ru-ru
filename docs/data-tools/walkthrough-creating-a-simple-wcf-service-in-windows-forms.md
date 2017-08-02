---
title: "Walkthrough: Creating and Accessing WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, walkthrough [Visual Studio]"
  - "WCF, Visual Studio tools for"
  - "WCF services"
  - "WCF services, walkthrough"
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 25
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing WCF Services
В этом пошаговом руководстве демонстрируется создание простой службы [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)], ее тестирование и последующий доступ к ней из приложения Windows Forms.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Создание службы  
  
#### Создание простой службы WCF  
  
1.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
2.  В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C\#** и щелкните **WCF** и **Библиотека службы WCF**.  Нажмите кнопку **ОК**, чтобы создать проект.  
  
     ![Проект библиотеки служб WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Будет создана работающая служба, которую можно протестировать и использовать.  Следующие два действия демонстрируют, как можно изменить метод по умолчанию для использования другого типа данных.  В реальном приложении необходимо также добавить к службе ее специальные функции.  
  
3.  ![Файл IService1](~/docs/data-tools/media/wcf2.png "wcf2")  
  
     В **Обозревателе решений** дважды щелкните файл IService1.vb или IService1.cs и найдите следующую строку:  
  
     [!code-cs[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]  
  
     Измените тип параметра `value` на `String`:  
  
     [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]  
  
     В приведенном выше коде обратите внимание на атрибуты `<OperationContract()>` или `[OperationContract]` .  Эти атрибуты обязательны для любого метода, предоставляемого службой.  
  
4.  ![Файл Service1](../data-tools/media/wcf3.png "wcf3")  
  
     В **Обозревателе решений** дважды щелкните файл Service1.vb или Service1.cs и найдите следующую строку:  
  
     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-cs[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]  
  
     Измените тип параметра значения на `String`:  
  
     [!code-cs[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]  
  
## Тестирование службы  
  
#### Создание простой службы WCF  
  
1.  Нажмите клавишу **F5**, чтобы запустить службу.  Будет показана форма **Тестовый клиент WCF**, которая загрузит службу.  
  
2.  В форме **Тестовый клиент WCF** дважды щелкните метод **GetData\(\)** в разделе **IService1**.  Будет открыта вкладка **GetData**.  
  
     ![Метод GetData&#40;&#41;](../data-tools/media/wcf4.png "wcf4")  
  
3.  В диалоговом окне **Запрос** выберите поле **Значение** и введите `Hello`.  
  
     ![Поле значения](../data-tools/media/wcf5.png "wcf5")  
  
4.  Нажмите кнопку **Вызвать**.  Если отображается диалоговое окно **Предупреждение системы безопасности**, нажмите кнопку **ОК**.  Результаты будут отображены в окне **Ответ**.  
  
     ![Результат в поле "Ответ"](../data-tools/media/wcf6.png "wcf6")  
  
5.  В меню **Файл** щелкните **Выход**, чтобы закрыть тестовую форму.  
  
## Доступ к службе  
  
#### Обращение к службе WCF  
  
1.  В меню **Файл** выберите команду **Добавить** , а затем **Создать проект**.  
  
2.  В диалоговом окне **Создать проект** разверните узел **Visual Basic** или **Visual C\#**, выберите узел **Windows** и выберите элемент **Приложение Windows Forms**.  Нажмите кнопку **ОК**, чтобы создать проект.  
  
     ![Проект приложения Windows Forms](../data-tools/media/wcf7.png "wcf7")  
  
3.  Щелкните правой кнопкой мыши **WindowsApplication1** и выберите команду **Добавить ссылку на службу**.  Откроется диалоговое окно **Добавление ссылки на службу**.  
  
4.  В диалоговом окне **Добавление ссылки на службу** щелкните элемент **Найти**.  
  
     ![Добавить ссылку на службу &#45; диалоговое окно](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** будет отображаться в области **Службы** .  
  
5.  Нажмите кнопку **ОК**, чтобы добавить ссылку на службу.  
  
#### Создание клиентского приложения  
  
1.  В **Обозревателе решений** дважды щелкните **Form1.vb** или **Form1.cs**, чтобы открыть конструктор Windows Forms, если он еще не открыт.  
  
2.  Из **Панели элементов** перетащите на форму элемент управления `TextBox`, элемент управления `Label` и элемент управления `Button`.  
  
     ![Добавление элементов управления на форму](../data-tools/media/wcf9.png "wcf9")  
  
3.  Дважды щелкните `Button` и добавьте следующий код в обработчик событий `Click`:  
  
     [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]  
  
4.  В **Обозревателе решений** щелкните правой кнопкой мыши **WindowsApplication1** и выберите команду **Назначить запускаемым проектом**.  
  
5.  Нажмите клавишу **F5**, чтобы запустить проект.  Введите любой текст и нажмите кнопку.  Будет отображена надпись «Введено:» с введенным ранее текстом.  
  
     ![Форма с результатом](~/docs/data-tools/media/wcf10.png "wcf10")  
  
## См. также  
 [Пример использования служб ASMX и WCF](http://msdn.microsoft.com/ru-ru/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)