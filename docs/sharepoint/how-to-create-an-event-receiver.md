---
title: "Практическое руководство. Создание приемника событий"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "приемники событий [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, приемники событий"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Практическое руководство. Создание приемника событий
  Создание *приемников событий* позволяет реагировать на взаимодействие пользователя с элементами SharePoint, такими как списки и элементы списков.  Например, код приемника событий может сработать, если изменить календарь или удалить имя из списка контактов.  Следуя описанным в этом разделе процедурам, можно узнать, как добавить приемник событий в экземпляр списка.  
  
 Для выполнения этих шагов требуется установленная [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и поддерживаемые версии Windows и SharePoint.  Для получения дополнительной информации см. [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Поскольку для данного примера требуется проект SharePoint, необходимо также выполнить процедуру, описанную в разделе [Пошаговое руководство. Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## Добавление приемника событий  
 Проект, созданный в [Пошаговое руководство. Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) включает пользовательские столбцы сайтов, пользовательский список и тип содержимого.  В следующем примере этот проект будет дополнен с помощью добавления простого обработчика событий \(приемника событий\) в экземпляр списка, чтобы продемонстрировать, как обрабатывать события, возникающие в элементах SharePoint, например, таких как списки.  
  
#### Добавление приемника событий в экземпляр списка  
  
1.  Откройте проект, созданный согласно инструкциям в разделе [Пошаговое руководство. Создание столбца сайта, типа содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  В **обозревателе решений** выберите узел проекта SharePoint, который называется **Clinic**.  
  
3.  В строке меню выберите **Проект**, **Добавить новый элемент**.  
  
4.  В области **Visual C\#** или **Visual Basic** разверните узел **SharePoint** и выберите элемент **2010**.  
  
5.  В области **Шаблоны** выберите **Приемник событий**, назовите его TestEventReceiver1, а затем нажмите кнопку **ОК**.  
  
     Появится окно **Мастер настройки SharePoint**.  
  
6.  В списке **Тип приемника событий:** выберите значение **События элемента списка**.  
  
7.  В списке **Элемент, который должен быть источником событий** выберите **Patients \(Clinic\\Patients\)**.  
  
8.  В списке **Обработать следующие события** установите флажок в пункте **Элемент добавлен** и нажмите кнопку **Готово**.  
  
     Файл с кодом нового приемника событий содержит только один метод с именем `ItemAdded`.  В следующем шаге в этот метод добавляется код, который именует каждый контакт "Scott Brown" по умолчанию.  
  
9. Замените существующий метод `ItemAdded` на следующий код и нажмите клавишу F5.  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Код выполнится и в веб\-браузере откроется сайт SharePoint.  
  
10. На панели быстрого запуска выберите ссылку **Пациенты** и затем выберите ссылку **Добавить новый элемент**.  
  
     Откроется форма ввода новых элементов.  
  
11. Введите данные в поля, а затем нажмите кнопку **Сохранить**.  
  
     После нажатия кнопки **Сохранить**, столбец **Patient Name** автоматически примет значение "Scott Brown".  
  
## См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  