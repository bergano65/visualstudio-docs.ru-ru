---
title: 'Как: Создание приемника событий | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ead81e01022c8f389ad6010c89d0e433b82c542e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-event-receiver"></a>Практическое руководство. Создание приемника событий
  Создав *приемников событий*, можно ответить, когда пользователь взаимодействует с элементами SharePoint, таких как списки и элементы списков. Например, код приемника событий может сработать, если пользователь изменит календарь или удалит имя из списка контактов. Следуя описанным в этом разделе процедурам, можно узнать, как добавить приемник событий в экземпляр списка.  
  
 Для выполнения этих шагов требуется установить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и иметь поддерживаемые версии Windows и SharePoint. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Так как в этом примере требуется проект SharePoint, необходимо также выполнить процедуру, описанную в разделе [Пошаговое руководство: Создание столбца сайта, тип содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## <a name="adding-an-event-receiver"></a>Добавление приемника событий  
 Проект, созданный в [Пошаговое руководство: Создание столбца сайта, тип содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) включает пользовательских столбцов сайта, настраиваемого списка и тип содержимого. В следующей процедуре этот проект будет дополнен путем добавления простого обработчика событий (приемника событий) в экземпляр списка, чтобы показать, как обрабатывать события, возникающие в элементах SharePoint, таких как списки.  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Чтобы добавить приемник событий в экземпляр списка  
  
1.  Откройте проект, созданный в [Пошаговое руководство: Создание столбца сайта, тип содержимого и списка для SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  В **обозревателе решений**, выберите узел проекта SharePoint, который называется **Clinic**.  
  
3.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
4.  В рамках одного **Visual C#** или **Visual Basic**, разверните **SharePoint** узел, а затем выберите **2010** элемента.  
  
5.  В **шаблоны** области, выберите **приемника событий**, назовите его **TestEventReceiver1**и нажмите кнопку **ОК** кнопки.  
  
     **Мастер настройки SharePoint** отображается.  
  
6.  В **какой тип приемника событий??** выберите **события элемента списка**.  
  
7.  В **элемент, который должен быть источником событий?** выберите **Patients (Clinic\Patients)**.  
  
8.  В **обрабатывать следующие события** списке, установите флажок рядом с **добавлен элемент**и нажмите кнопку **Готово** кнопки.  
  
     Файл кода для нового приемника событий содержит только один метод с именем `ItemAdded`. На следующем шаге вы добавите код в этот метод, чтобы каждому контакту имя Scott Brown по умолчанию.  
  
9. Замените существующий метод `ItemAdded` на следующий код и нажмите клавишу F5.  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Код выполнится, и в веб-браузере откроется сайт SharePoint.  
  
10. На панели быстрого запуска выберите **пациентов** связь, а затем выберите **Добавление нового элемента** ссылку.  
  
     Откроется форма ввода новых элементов.  
  
11. Введите данные в полях и нажмите кнопку **Сохранить** кнопки.  
  
     После выбора **Сохранить** кнопки, **Patient Name** автоматически обновляет столбец с именем Scott Brown.  
  
## <a name="see-also"></a>См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  